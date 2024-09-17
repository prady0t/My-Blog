---

title: "GSoC week 1 and 2"

date: 2024-06-03

  

---

![GSoC Banner](/GSoC_Banner.png)
<img src = "/GSoC_Banner.png">

  

Recently I got selected for the Google Summer of Code program. I've been working with PyBaMM (under the NumFOCUS umbrella) to improve their test suite. This blog will touch more on my experience of getting accepted as a GSoC student and my work till now and for the future at PyBaMM.

### Getting Selected and Community Bonding

I started contributing to PyBaMM in November last year.  Initially, it was difficult to navigate through the codebase, but the mentors were pretty chilled out and helped me a lot. Part of the reason why I stuck around (other than my love for Python-related projects) was the helpful people that I found here. I've learned a lot contributing to this project and it's only going to increase from here.

The community bonding phase was really helpful. Although most of the time I had exams so was not able to do meetings very frequently, mentors were pretty supportive of this. We had a meeting where we discussed how we will carry forward with this project, some prerequisites that need to be done and overall introduction to the PyBaMM team.

### What is PyBaMM?


![PyBaMM Banner](/Pybamm_banner.png)
<img src = "/Pybamm_banner.png">


PyBaMM (Python Battery Mathematical Modelling) is a tool for fast and flexible simulations of battery models. It provides an open-source framework for multi-institutional, interdisciplinary collaboration. PyBaMM offers improved collaboration and research impact in battery modelling by creating a modular framework through which either existing or new tools can be combined to solve continuum models for batteries. You can learn more about PyBaMM from the official docs [here](https://pybamm.org/).


### What am I working on?


PyBaMM is very active with its infrastructure-related changes. Maintainers actively look for the latest changes in the scientific Python community and try to keep up with them. My project deals with improvements related to the testing infrastructure at PyBaMM. PyBaMM currently has all their tests written in `unittest` style tests. Unittest is a framework included in the Python standard library and is used by many Python-based projects, but it is now slowly getting replaced by `pytest`. `pytest` is a popular third-party testing framework known for its simplicity, powerful test discovery, and expressive syntax.

The good news is, `pytest` supports unittest style tests out of the box. So the existing tests (written in `unittest` style test) will work with `pytest`. Even before GSoC, I was working on using `pytest` to run all the tests. The single biggest advantage is that `pytest` offers parallel execution of tests using `pytest-xdist` plugin. This drastically improves the time taken to run tests. 

We already merged a PR that allows unit tests to run with `pytest`. In the first week, I also managed to run integration tests with it. It was not as straightforward as unit-tests. The main problem was with running integration tests in parallel. Most of the integration tests were dumping the JSON data to the same file. Running them parallel resulted in race conditions and the JSON file was getting corrupted. To overcome this issue we decided to use a `uuid` for each filename being generated during tests. This helped us run all integration tests without any skips in parallel with whopping speed gains. You can have a look at my [PR](https://github.com/pybamm-team/PyBaMM/pull/4125). 

In future, my work would be mostly rewriting `unittest` style tests to `pytest`. Doing so manually would be tedious so we will look into tools that can help automate the process. We also want to implement property-based testing using `hypothesis` framework. Documenting this whole process can be helpful for other projects planning such migrations in future. Please feel free read more about my [GSoC project](https://summerofcode.withgoogle.com/programs/2024/projects/gnFfAnqb).


Note: I'll be writing fortnightly blogs to keep things updated. If you are interested in this project, you can come back every two weeks to check out the progress. 