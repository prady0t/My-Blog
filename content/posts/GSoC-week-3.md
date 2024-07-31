---

title: "GSoC week 4 and 5"

date: 2024-07-27

  

---

![GSoC Banner](/GSoC_Banner.png)
<img src = "/GSoC_Banner.png">

This blog will cover the fourth and fifth week as a GSoC student.

### Work so far and for the coming weeks.

- Finally the [PR](https://github.com/pybamm-team/PyBaMM/pull/4180) to remove `run-test.py` file (mentioned in previous blog) got merged! With this we are now using nox for all testing and virtual environment related stuff. We are also now using pytest markers for running tests. Interesting part is they are not explicitly used anywhere in the codebase by using `pytest.mark` (except once for running example scripts but even there it's used very cleverly) but rather declared explicitly in `conftest.py` file according to the nodeID (tests location, marked unit for tests in `unit` folder and similarly for integration).

- Test migration : Lots of tests have been migrated to pytest so for. We initially had a total of around 160 files and we have already migrated close to 100 files! Migrating these files is pretty straightforward. We don't have to do a lot of changes. We use an open-source tool called [pytestify](https://github.com/dannysepler/pytestify) which converts the commonly used unittest style python code to pytest. Although not perfect, it helps in syntactical conversion and to cut down manual repetitive work. I'm also planning on improving this tool (this might be my work outside GSoC) for future developers and testers. You can refer to the PR's listed below : 

    https://github.com/pybamm-team/PyBaMM/pull/4285

    https://github.com/pybamm-team/PyBaMM/pull/4264

    https://github.com/pybamm-team/PyBaMM/pull/4238

- Dealing with non deterministic tests : Few tests in PyBaMM are non deterministic i.e. it produce different output when given similar same input. It's always a pain to test these. Earlier we had a custom TestCase file in the unittest testing framework. This Testcase file had a Metaclass that wraps all class methods with FixRandomSeed(), this function wraps a method so that the random seed is set to a hash of the method name. Now that we are determined to migrate, we are removing this file and can be easily dealt with using pytest fixtures. [This](https://github.com/pybamm-team/PyBaMM/pull/4231) PR deals with similar changes to the codebase.

- Codacy false flagging : Another problem that we faced was with Codacy falsely flagging the assert statement from test. Codacy doesn't have a rule to configure it per path, we added a bandit.yml file to ignore asserts from everywhere, then used ruff to ignore test folders and find `assert` statements elsewhere. [This](https://github.com/pybamm-team/PyBaMM/pull/4236) changes also helped ruff to identify asserts in the codebase.

- Using tempfile : Referring to a [PR](https://github.com/pybamm-team/PyBaMM/pull/4125) in earlier blog, we used pytest for Integration test and ran multiple tests parallely. In the process lot of json files were getting created (which were supposed to get deleted by the end of test suit but if the test suit failed, some of the files didn't). To get rid of this files we used [tempfile](https://github.com/pybamm-team/PyBaMM/pull/4270/files) instead. We no longer need uuid to generate unique file names as `tempfile` handles race conditions by itself.