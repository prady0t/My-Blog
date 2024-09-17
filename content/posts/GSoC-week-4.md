---

title: "GSoC week 7 and 8"

date: 2024-08-10

  

---

![GSoC Banner](/GSoC_Banner.png)
<img src = "/GSoC_Banner.png">

This blog will cover the seventh and eighth week as a GSoC student.

### Work so far and for the coming weeks.

- Moving all the integration test files to pytest : Finally all the integration test files have been migrated to pytest. With this integration we also ensure not using unittest anywhere in the integration test suite and moving to pytest ecosystem. There were some large files that needed a bit of time as well as some which were fairly straightforward (using numpy testing so not much changes were required). To know more follow the [PR](https://github.com/pybamm-team/PyBaMM/pull/4285).

- Annotating GitHub-Action failures : One essential addition was using [pytest-github-actions-annotate-failures](https://github.com/pytest-dev/pytest-github-actions-annotate-failures) to annotate failures created by pytest running tests inside github-actions. This really helps with pointing out the lines (or tests) that created this failure inside the github UI itself. You don't have to look inside lengthy logs anymore. Follow the [PR](https://github.com/pybamm-team/PyBaMM/pull/4294) to know more.

- Moving to `src` layout : Finally a PR to move to `src` layer has been made. This includes all test files migration to a src folder along with related changes to file paths. With this we remove the flat layout. We now will be able to test the build wheel with `cibuildwheel` inside the CI itself which will be covered in the upcoming PR. Follow the [PR](https://github.com/pybamm-team/PyBaMM/pull/4311) to know more.