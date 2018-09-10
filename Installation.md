# Installation

Installation of `pyfor` requires two things:

1. `conda`
2. `git`

Before we begin, we need to download a copy of `conda`. This program will allow us to easily install all of `pyfor`'s dependencies. We can get `conda` in two ways. First, and arguably the simplest way is to install Miniconda, which is a reduced version of a larger software suite called Anaconda. I suggest this route if you want to get started quickly. If you want to install Anaconda, go right ahead, it is a superset of Miniconda.

## `conda` and Environments

What if I told you `pyfor` doesn't even need Python to run? Well, I would only be sort of correct. It turns out that `conda` will handle the installation of Python itself for us. `conda` is a multi-platform package manager that can install binaries and Python packages for us according to the operating system we are using. It also offers mechanisms for managing Python environments. An environment is an important tool for Python users, and may be a bit different for those of you coming from an R background.

Imagine a scenario in which you have several projects that you are working on concurrently, all of which use different packages and different Python versions. We would want a system such that we can segregate these different set-ups into discrete partitions. This way, our packages and their dependencies will not interfere with eachother. Were you ever writing an R script and had one package mask the functionality of another because you were using the wrong version? With environments we can avoid this catastrophe. `conda` enables us to create, manage and modify environments. Another thing that is useful about environments is that I can share environments I make with someone else. In the case of `pyfor` I have already created an environment for you that has all of the required packages so you can use it. If you are curious what is required, check the contents of `pyfor/environment.yml`. For those of you familiar with Python you will see many familiar faces, `numpy`, `pandas`, etc.

## The Installation Procedure

Finally, we can begin our installation. First, we clone the GitHub repository that has `pyfor` in it:

```{}
git clone https://github.com/brycefrank/pyfor.git
```

Then, we enter the newly cloned repository and create our environement:

```{}
cd pyfor
conda env create environment.yml
```

This tells `conda` to create an environment based off of the `environment.yml` file I made for you. This creates an environment called `pyfor_env`. Now, we activate this environment and install `pyfor` itself into the Python interpreter. Expect this step to take a while. `conda` does a lot of computational work to ensure that it is downloading compatible versions and dependencies of packages for you.

```{}
# For Linux/MacOS
source activate pyfor_env

# For Windows
activate pyfor_env

pip install .
```

This activates the `pyfor_env` environment, which knows to use a particular Python interpreter specific to the environment. The final command instructs the Python-specific package manager, `pip` to install `pyfor` into this interpreter. This final step is what allows us to `import pyfor` in a given script.

## The Development Environment

Of course, no good Python programmer is without an IDE and efficient development and analysis with `pyfor` depends on a good pick for your IDE.

### PyCharm

`pyfor` was primarily developed using the excellent PyCharm Community Edition (and Professional Edition in some cases). The latest version, 2018.2, provides direct access to an interactive `IPython` console. It is cross platform and free to use. It is, however, a bit of a heavy application. If you plan on developing robust, repeat-use Python scripts and modules, I suggest this option. To install PyCharm go to their [website](https://www.jetbrains.com/pycharm/) and follow the installation instructions.

### Jupyter Notebook

For more lightweight analysis, I suggest taking advantage of Jupyter notebooks. Jupyter notebooks are a popular platform in data science for creating quick analysis scripts that are nicely coupled with visualization libraries (that `pyfor` takes advantage of already). If you want to use Jupyter notebooks, it does require some modification of your `conda` environment to do so, but nothing terrible complex. Below are a few instructions to get set up.

First, install the `jupyter` and `nb_conda` packages in your `pyfor_env` environment:

```
conda install jupyter nb_conda -n pyfor_env
```

Then, go to a directory in which you would like to conduct analysis with your `pyfor_env` environment activated and start Jupyter with the following command:

```
jupyter notebook
```

### Jupyter Lab

Despite Jupyter's simplicity, it is a very productive tool for routine processing tasks and interactive analysis.

A new iteration of Jupyter notebooks is Jupyter lab, which allows for a more flexible development environment contained within your browser.

[Expand on Jupyter lab]
