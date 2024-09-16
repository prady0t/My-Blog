---

title: "GSoC week 9 and 10"

date: 2024-08-24

  

---

![GSoC Banner](/GSoC_Banner.png)
<img src = "/GSoC_Banner.png">

This blog will cover the ninth and tenth week as a GSoC student.

### Work so far and for the coming weeks.

- Migrating tests to pytest part 5 : Almost 20 more files were moved to pytest. With this almost half of the unit tests are migrated to pytest! You can follow the [PR](https://github.com/pybamm-team/PyBaMM/pull/4333) to know more.

- Using posargs to pass arguments to nox sessions : We can now give inputs to `tests` nox session. This makes pybamm's testing infrastructure more modular. It can take inputs any number of files, class or function names and run only those specifically. For example user can now pass `nox -s tests -- tests/unit/test_expression_tree/test_binary_operators.py` to just run tests inside `test_binary_operators.py`. You can follow the [PR](https://github.com/pybamm-team/PyBaMM/pull/4334) to know more.

- Testing the build wheels with `cibuildwheel` : After moving to src layout from flat layout, we were ready to implement `cibuildwheel` and test the wheel in CI. To improve the testing time, we just tested if `test_idaklu_solver.py` runs without any error using the `cibw` pytest marker. This is run in CI using `pytest -m cibw`. Follow the [PR](https://github.com/pybamm-team/PyBaMM/pull/4341) to know more.