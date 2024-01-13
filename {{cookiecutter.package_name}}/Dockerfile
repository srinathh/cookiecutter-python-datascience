FROM python:{{cookiecutter.python_version}}

WORKDIR /app

COPY . .

RUN pip install -e .
ENTRYPOINT [ "{{cookiecutter.package_name}}" ]
