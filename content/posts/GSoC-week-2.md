---

title: "GSoC week 2 and 3"

date: 2024-06-29

  

---

![GSoC Banner](/GSoC_Banner.png)
<img src = "/GSoC_Banner.png">

This blog will be about the work I did and interesting stuff I found in these two weeks as a GSoC student.

### Work so far and for the coming weeks.

In these two weeks we heavily planned and implemented lot of infrastructural changes. These changes may not effect general users of PyBaMM, but 
developers will surely benefit a lot from them. I also had a taste of how interrelated PRs can be an issue (although not so much in my case), I'll
explain more about it later.

Let's break down the work:

- Removing `run-tests.py` file: Most Python projects use a `run-tests.py`, which is used to handle command-line inputs while running tests. PyBaMM already had 
`noxfile.py`. This file is used to handle `nox` sessions.`nox` is a command-line tool that automates testing in multiple Python environments, similar to `tox`. So
we already had multiple nox sessions for different testing conditions. `noxfile` in pybamm project pointed to `run-tests.py` file and hence the work was to  completely remove the legacy code in `run-test.py` file and use nox for everything. 
  

  To do this, we had to put markers for every tests. Pytest has a feature that enables users to mark tests with specific names and that particular tests can be 
  handled by `conftest.py` file. For example let's say I want to have tests marked with label `foo`, and to run them only when specified so. To do this we can mark 
  the test function by adding decorator `@pytest.mark.foo` and run them with `pytest --foo`. These inputs are handled by `conftest.py` file. These markers can also be defined implicitly inside `conftest.py` file. That is an even better approach, since now we don't have to add decorators to every test function and if someone 
  forgets to specify any marker for a test, we can still get away with it since `conftest.py` adds markets while collecting tests. You can read more about pytest markers from the official [docs](https://docs.pytest.org/en/7.1.x/example/markers.html#:~:text=with%20parametrize.-,Custom%20marker%20and%20command%20line%20option%20to%20control%20test%20runs,-%C2%B6). This is still a work in progress at time of writing this blog, you can have a [look](https://github.com/pybamm-team/PyBaMM/pull/4180) to know more about it.


- Trying to implement `CIBW_TEST_COMMAND` for testing wheels and moving to a `src` layout : `cibuildwheel` simplifies the creation of Python Wheels for the different platforms and Python versions through CI workflows. `CIBW_TEST_COMMAND` option enables us to test the wheels before uploading it to `pypi`. It imports the project from the wheel and not from project root and runs the tests against it. Problem here was PyBaMM follows a flat layout i.e. `pybamm` lives in the project root. Problem here is, while testing both the wheel and project directory lives at the same place and thus while importing, pybamm imports from `pybamm` folder. This leads to few of the tests getting skipped (tests for IDAKLU slover, which depends upon it's availability and is not present inside `pybamm` folder). Hence we have decided to switch to a `src` layout. [This](https://github.com/prady0t/PyBaMM/pull/1) PR is on my local fork and you can see how both these changes effect the behavior of `CIBW_TEST_COMMAND` in CI runs.

- Finally started migrating tests to `pytest` : I tried migrating `test_util.py` from unittest to pytest. I used a tool called [pytestify](https://github.com/dannysepler/pytestify) that was useful for syntactical conversion but obviously lot of stuff also had to be done manually. You can have a look at [this](https://github.com/pybamm-team/PyBaMM/pull/4214) PR.

This is mostly the work I did in these weeks apart from reading and learning more about pytest advance features such as `fixtures`. I also came across a term called `monkeypatch` and `metaprogramming` which I will learn more about in the coming weeks. (Just wanted to use these words )

Work in the coming weeks work will be more focused on (apart from the above mentioned pending PR's) converting `unittest` to `pytest` and how we are trying to automate and streamline this whole process.

Note: I’ll be writing fortnightly blogs to keep things updated. If you are interested in this project, you can come back every two weeks to check out the progress.