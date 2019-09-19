

## notes

There are two ways to load python modules: through an environment.yml file (which loads through Anaconda) or through a requirements.txt file (which still somehow loads through conda)

These have different formatting requirements. The tricky part is that it's better if this file is built with the project, rather than being reconstructed afterwards. This is because some of the modules need to have specific version numbers, and it takes a bit of trying to get those to work after the fact. For this project I've used a requirements.txt file, which also needs an additional file called runtime.txt to specify the python version. This project was built in python2.7, which will not be supported as of Jan.2020.

### environment.yml example

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

### requirements.txt example

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
