# {{ cookiecutter.project_name.title() }}

[![pdm-managed](https://img.shields.io/badge/pdm-managed-blueviolet)](https://pdm.fming.dev)
[![code style black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![imports isort](https://img.shields.io/badge/%20imports-isort-%231674b1)](https://pycqa.github.io/isort/)
[![formatter docformatter](https://img.shields.io/badge/%20formatter-docformatter-fedcba.svg)](https://github.com/PyCQA/docformatter)
[![docstyle numpy](https://img.shields.io/badge/%20style-numpy-459db9.svg)](https://numpydoc.readthedocs.io/en/latest/format.html)
[![pre-commit enabled](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)

## Repo Structure

```
.
├── notebooks
├── scripts
├── src
│  └── {{ cookiecutter.package_name }}
├── tests
├── .gitignore
├── .pre-commit-config.yaml
├── pdm.lock
├── pyproject.toml
└── README.md
```

* [`notebooks`]() contains the exploratory notebooks.
* [`scripts`]() shell scripts.
* [`src`]() contains the code.
    * [`{{ cookiecutter.package_name }}`]() is the dedicated Python package.
* [`tests`]() contains the test for the package.
* [`.gitignore`]() contains the ignored files.
* [`.pre-commit-config.yaml`]() has the hooks for [`pre-commit`](https://github.com/pre-commit/pre-commit).
* [`pdm.lock`]() is the lockfile that `pdm` uses to create a copy of the environment.
* [`pyproject.toml`]() contains the specifications to build a replica of the environment used for this project.

## Setup

The setup is explained in greater detail in the paragraph below. To get up and running, do the following:

1. Install `pdm` in one of the following ways:

```bash
# with your package manager, e.g. brew for macos
brew install pdm

# with pipx
pipx install pdm

# with pip
pip install -U pdm
```

2. Execute the following command inside the project folder:

```bash
pdm install
```

3. Configure `pdm` for Your IDE. Since `pdm` is still not as widely supported as `pipenv` or `poetry`, but
   the [official documentation](https://pdm.fming.dev/#use-with-ide) explains how to configure them:
    1. For PyCharm specifically, you need
       to [mark as Sources Root](https://www.jetbrains.com/help/pycharm/configuring-project-structure.html#mark-dir-project-view)
       the `__pypackages__/{{ cookiecutter.python_version }}/lib` folder.
    2. As the project interpreter, you will need to select the same Python version specified in the `pyproject.toml`.
        * To support multiple Python versions on your machine, [`pyenv`](https://github.com/pyenv/pyenv) is recommended.

:warning: If you need to run command-line executables installed with `pdm`, such as `pytest` or `jupyter notebook`, you need to run `pdm run pytest <args>`.
Alternatively, you can use stuff like [`direnv`](https://direnv.net) to automatically prepend `__pypackages__/{{ cookiecutter.python_version }}/bin` to your `$PATH`.

<details>
   <summary><h3>Why `pdm`: The Other Dependency Managers</h3></summary>

There are a lot of Python dependency management tools - each with its own set of trade-offs. `conda` is painfully slow
and does not offer many of the capabilities that dependency managers display today - starting from the user
interface. [`mamba`](https://github.com/mamba-org/mamba) is a worthy replacement that can be installed in your
base `conda` environment. However, this does not solve problems such as cross-platform compatibility with Unix and
Windows OS. To ensure maximum compatibility, `pip` and virtualenv-based managers were chosen. Crucially, `conda` does
not support differentiation between production and development dependencies: tools such as `pytest` and `tox` will end
up in the same environment specification file - while they should be separated.

`poetry` does not suffer from these weaknesses, as it is production/build oriented. Yet, it was not considered as it
overly-uses upper version constraints (see [here](https://iscinumpy.dev/post/bound-version-constraints/)
and [here](https://iscinumpy.dev/post/poetry-versions/)) and, crucially, **does not plan to follow future PEP
standards**. [`pipenv`](https://github.com/pypa/pipenv) does not, but requires running a shell subprocess to work. `pdm`
is the latest addition in Python dependency management and it is developed independently by a member of PyPA, i.e. the
Python Packaging Authority. It is by far the most complete, albeit it lacks mainstream support that all the other
managers. `pipenv` and `pdm` support PEP standards and adopt the `pyproject.toml` file specification to ensure
deterministic builds.

</details>
