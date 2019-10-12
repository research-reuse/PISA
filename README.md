# PISA

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/research-reuse/PISA/master?filepath=pisa_basic%2Fnotebooks%2Fpisa_project_part1.ipynb)

## Introduction

This repository has been forked from <https://github.com/mklajnerok/PISA> to be used as a research reproducibility exemplar for the [Curating Data Sets for Reproducibility](https://research-reuse.github.io/) workshop at the [Canadian Data Curation Forum](https://data-curation.github.io/), held on October 16-18, 2019 in Hamilton, ON.

While we have tried to change as little as possible, there were things that needed to be fixed in order to have the project run in [MyBinder](https://mybinder.org/). A folder called [binder](https://github.com/research-reuse/PISA/tree/master/binder) was added to hold the files required for the MyBinder implementation. These are the configuration files that allow the [PISA Jupyter notebook file] (https://github.com/research-reuse/PISA/tree/master/pisa_basic/notebooks) to be packaged as a container file. The first file `requirements.txt` is a dependencies file, listing all of the Python modules that are required to run the code. The second file `runtime.txt` specifies which Python version was used to write the code.

In addition, there is an error in the 10th code cell of the [pisa_project_part1.ipynb](https://github.com/research-reuse/PISA/tree/master/pisa_basic/notebooks). This error has something to do with [numpy](https://numpy.org/) and floats, but it's not something that we've been able to fix.

### Notes on Dependencies

There are two ways to load Python modules: through an `environment.yml` file (which loads through Anaconda) or through a `requirements.txt` file (which still somehow loads through Conda).

These have different formatting requirements. The tricky part is that it's better if the dependencies file is built with the project, rather than being reconstructed afterwards. This is because some of the modules need to have specific version numbers, and it takes a bit of trying to get those to work after the fact. Determining the specific module versions was time-intensive (and frustrating). 

At the time of file creation, running the following commands would be extremely helpful:
```
IPython.sys_info() # requires importing the IPython module, prints detailed information about the runtime environment
pip freeze > requirements.txt # prints a list of all dependencies, 
                              # refer to https://pip.pypa.io/en/stable/reference/pip_freeze/ for specifics
```

For this project we've used a `requirements.txt file`, which also needs an additional file called `runtime.txt` to specify the Python version. This project was built in Python2.7, which will not be supported as of Jan 2020. Below is a sample set of each file, showing the formatting differences between the two.

#### environment.yml example

```
channels:
  - conda-forge
dependencies:
  - conda==4.7.12
  - python
  - numpy>=1.11
  - pip
  - scipy>=0.18
  - patsy>=0.4.0
  - cython>=0.24
  - pip:
    - wbdata==0.2.7
    - statsmodels.formula.api==0.10
    - pandas>=0.19
    - matplotlib
```

#### requirements.txt example

```
numpy==1.11
scipy==0.18
patsy==0.4.0
cython==0.24
wbdata==0.2.7
pandas==0.19
matplotlib
pycountry
```

