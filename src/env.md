# Environments

## What is an environment?
A Paxy environment is like a docker container. It allows you to use a specific version of a package without installing it globally. This is useful for testing, or if you want to use a different version of a package than the one installed globally. It's also useful if the package is temporary. For example, if you need a specific version of python, but you don't usually use python, you can create an environment for that version of python, and when you're done it is automatically removed.

## How do I create an environment?
Environments are created with `paxy env {package(s)}`. For example, to create an environment with python 3.6, you would run `paxy env python@3.6`. You will be provided with an instance of your system shell, or the shell specified in your configuration. You can then use the package as you would normally. For example, to install a python package, you would run `pip install {package}`. You can specify more than one package to the command.

## How are environment packages stored?
They are stored on the system as regular packages, with the env flag set. A `paxy clean` command will remove them permanently.