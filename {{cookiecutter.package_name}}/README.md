{{cookiecutter.package_name}}
===============================
{{cookiecutter.package_description}}


Package Structure
-----------------
- **Libraries** provided by the package should be developed inside `src/{{cookiecutter.package_name}}`
  - A `hello_world()` function is provided inside `src/{{cookiecutter.package_name}}/__init__.py` as an example
  - The Library packages can be installed for local develoment with `pip install -e .[dev]`
  - The development bui

- **Executables** provided by the package should be developed inside `src/bin`
  - A default executable is provided under `src/bin/main.py` with the entrypoint `main()`
  - To run this executable from console, run `{{cookiecutter.package_name}}`. It calls the `helllo_world()` function
  - The executable name and entrypoint are configured in `pyproject.toml` under `[project.scripts]`

- **Tests** shoudl be written under `tests` folder
  - Tests are deliberately kept outside the source tree to ensure tests run only after package installation
  - The provided `test_sample.py` tests that the supplied `hello_world()` behaves as expected

- **Data** if needed should be placed in the `data` folder. All contents are ignored

- **Notebooks** should be developed inside `notebooks`. They will work only if package is installed.

```
{{cookiecutter.package_name}}
├── data
│   └── .gitkeep
├── notebooks
│   └── .gitkeep
├── src
│   ├── bin
│   │   ├── __init__.py
│   │   └── main.py
│   └── {{cookiecutter.package_name}}
│       └── __init__.py
└── tests
│   └── test_sample.py
├── .gitignore
├── Dockerfile
├── pyproject.toml
└── README.md
```


Development
-----------
Clone the repository to the development machine, create a virtual environment and install
the packages locally for development. Installing with the `.[dev]` option also installs
`ipykernel` and `pytest` to allow for experimentation with notebooks and unit testing.

```
conda create --name {{cookiecutter.package_name}} python={{cookiecutter.python_version}}
conda activate {{cookiecutter.package_name}}
pip install -e .[dev]
```

Testing
-------
`Pytest` can be used to run the tests in the `tests` folder
````
pytest
```

Executable
----------
`pyproject.toml` by default installs `{{cookiecutter.package_name}}` as an executable
command from the shell or command line.
```
{{cookiecutter.package_name}}
```

Docker
------
To containarize your application, simply use standard `docker build` and `docker run` commands.
It assumes the executable named `{{cookiecutter.package_name}}` is the default entry point.

```
docker build -t {{cookiecutter.package_name}}:latest .
docker run {{cookiecutter.package_name}}:latest
```

Authors
-------
`{{ cookiecutter.author_name }} <{{ cookiecutter.author_email }}>`_.
