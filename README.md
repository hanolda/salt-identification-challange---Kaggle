[![](https://travis-ci.org/Statoil/data-science-template.svg?branch=master)](https://travis-ci.org/Statoil/data-science-template?branch=master)
[![Coverage Status](https://coveralls.io/repos/github/Statoil/data-science-template/badge.svg?branch=master)](https://coveralls.io/github/Statoil/data-science-template?branch=master)

# Project Kaggle competition. 
## TGS Salt Identification Challenge. Segment salt deposits beneath the Earth's surface.

This is a data science projects based on Kaggle competition: TGS Salt Identification Challenge. Segment salt deposits beneath the Earth's surface.

## Overview

Several areas of Earth with large accumulations of oil and gas also have huge deposits of salt below the surface.

But unfortunately, knowing where large salt deposits are precisely is very difficult. Professional seismic imaging still requires expert human interpretation of salt bodies. This leads to very subjective, highly variable renderings. More alarmingly, it leads to potentially dangerous situations for oil and gas company drillers.

To create the most accurate seismic images and 3D renderings, TGS (the world’s leading geoscience data company) is hoping Kaggle’s machine learning community will be able to build an algorithm that automatically and accurately identifies if a subsurface target is salt or not.

## Evaluation

This competition is evaluated on the mean average precision at different intersection over union (IoU) thresholds. 

## Data Description

### Background
Seismic data is collected using reflection seismology, or seismic reflection. The method requires a controlled seismic source of energy, such as compressed air or a seismic vibrator, and sensors record the reflection from rock interfaces within the subsurface. The recorded data is then processed to create a 3D view of earth’s interior. Reflection seismology is similar to X-ray, sonar and echolocation.

A seismic image is produced from imaging the reflection coming from rock boundaries. The seismic image shows the boundaries between different rock types. In theory, the strength of reflection is directly proportional to the difference in the physical properties on either sides of the interface. While seismic images show rock boundaries, they don't say much about the rock themselves; some rocks are easy to identify while some are difficult.

There are several areas of the world where there are vast quantities of salt in the subsurface. One of the challenges of seismic imaging is to identify the part of subsurface which is salt. Salt has characteristics that makes it both simple and hard to identify. Salt density is usually 2.14 g/cc which is lower than most surrounding rocks. The seismic velocity of salt is 4.5 km/sec, which is usually faster than its surrounding rocks. This difference creates a sharp reflection at the salt-sediment interface. Usually salt is an amorphous rock without much internal structure. This means that there is typically not much reflectivity inside the salt, unless there are sediments trapped inside it. The unusually high seismic velocity of salt can create problems with seismic imaging.

### Data
The data is a set of images chosen at various locations chosen at random in the subsurface. The images are 101 x 101 pixels and each pixel is classified as either salt or sediment. In addition to the seismic images, the depth of the imaged location is provided for each image. The goal of the competition is to segment regions that contain salt. The data is 200 MB zip cointating training and test sets.

You should then modify the contents of your new copy as suited (alternatively before adding hte files to git). In particular you might want to do the following:

# Project Template Overview
* Update this readme file to describe your project including setup, configuration and usage. You might also delete this Getting Started section once you have considered the steps below
* If using Travis for CI then modify .travis.yml as needed, if not then delete this file / replace with another for e.g. Jenkins. 
* Change or delete the LICENSE file if your terms are different.
* Modify conda_env.yml with a project specific name
* Create a [requirements.txt](https://pip.pypa.io/en/stable/user_guide/) file for any non Conda packages.
* Rename src\examplepackage to something more relevant to your project (e.g. src\<projectname>). This will also require corresponding changes in:
   * tests\test_examplepackage_examplemodule.py - import statement 
   * notebooks\example.ipynb - import statement
   * setup.py - packages list



### Setup
1. Install git and checkout the [git code repository]
2. Install [anaconda] python version 3.6+
3. Change working directory into the git code repository root
4. Create the self contained conda environment. In a terminal go to the git code repository root and enter the command:

   `conda env create --file conda_env.yml`

5. Any python modules under src need to be available to other scripts. This can be done in a couple of ways. You can 
setup and install the python modules by executing the setup.py command below which will install the packages to the 
conda environments site-packages folder but with a symlink to the src folder so modifications are reflected immediately. 

   `python setup.py develop`
   
    As an alternative you may prefer to set the python path directly from the console, within notebooks, test scripts 
    etc. From Pycharm you can also right click the src folder and select the _Mark Directory As | Source Root_ option.

6. .. Place your own project specific setup steps here e.g. copying data files ...

When distributing your module, you can create a Python egg with the command `python setup.py bdist_egg` and upload the egg.

NOTE: When working in the project notebooks from within the Statoil network, you may need to include the lines below if your proxy is not otherwise setup.

`os.environ['HTTP_PROXY']="http://www-proxy.statoil.no:80"`<br />
`os.environ['HTTPS_PROXY']="http://www-proxy.statoil.no:80"`

### Using the Python Conda environment

Once the Python Conda environment has been set up, you can

* Activate the environment using the following command in a terminal window:

  * Windows: `activate my_environment`
  * Linux, OS X: `source activate my_environment`
  * The __environment is activated per terminal session__, so you must activate it every time you open terminal.

* Deactivate the environment using the following command in a terminal window:

  * Windows: `deactivate my_environment`
  * Linux, OS X: `source deactivate my_environment`
               
* Delete the environment using the command (can't be undone):

  * `conda remove --name my_environment --all`

### Initial File Structure

```
├── .gitignore               <- Files that should be ignored by git. Add seperate .gitignore files in sub folders if 
│                               needed
├── .travis.yml              <- Travis CI build file (used for validating this template). Internally we might use 
│                               Jenkins?
├── conda_env.yml            <- Conda environment definition for ensuring consistent setup across environments
├── LICENSE
├── README.md                <- The top-level README for developers using this project.
├── requirements.txt         <- The requirements file for reproducing the analysis environment, e.g.
│                               generated with `pip freeze > requirements.txt`. Might not be needed if using conda.
├── setup.py                 <- Metadata about your project for easy distribution.
│
├── data
│   ├── interim_[desc]       <- Interim files - give these folders whatever name makes sense.
│   ├── processed            <- The final, canonical data sets for modeling.
│   ├── raw                  <- The original, immutable data dump.
│   └── temp                 <- Temporary files.
│
├── docs                     <- Any specific documentation (try ideally to keep to README.md)
│   └── process_documentation.mf  <- Standard template for documenting process and decisions.
│
├── examples                 <- Add folders as needed e.g. examples, eda, use case
│
├── extras                   <- Miscellaneous extras.
│   └── add_explorer_context_shortcuts.reg    <- Adds additional Windows Explorer context menus for starting jupyter.
│
├── notebooks                <- Notebooks for analysis and testing
│   ├── eda                  <- Notebooks for EDA
│   │   └── example.ipynb    <- Example python notebook
│   ├── features             <- Notebooks for generating and analysing features (1 per feature)
│   ├── modelling            <- Notebooks for modelling
│   └── preprocessing        <- Notebooks for Preprocessing 
│
├── reporting                <- Solutions for reporting of results
│   ├── webapp               <- Flask based template for displaying content including text and graphs
│   └── README.md            <- Information on usage and setup of the webapp sample and more
│
├── src                      <- Code for use in this project.
│   └── examplepackage       <- Example python package - place shared code in such a package
│       ├── __init__.py      <- Python package initialisation
│       ├── examplemodule.py <- Example module with functions and naming / commenting best practices
│       ├── features.py      <- Feature engineering functionality
│       ├── io.py            <- IO functionality
│       └── pipeline.py      <- Pipeline functionality
│
└── tests                    <- Test cases (named after module)
    ├── test_notebook.py     <- Example testing that Jupyter notebooks run without errors
    ├── examplepackage       <- examplepackage tests
        ├── examplemodule    <- examplemodule tests (1 file per method tested)
        ├── features         <- features tests
        ├── io               <- io tests
        └── pipeline         <- pipeline tests
```

### Testing
Reproducability and the correct functioning of code are essential to avoid wasted time. If a code block is copied more 
than once then it should be placed into a common script / module under src and unit tests added. The same applies for 
any other non trivial code to ensure the correct functioning.

To run tests, install pytest using pip or conda (should have been setup already if you used the conda_env.yml file) and 
then from the repository root run
 
```pytest```




