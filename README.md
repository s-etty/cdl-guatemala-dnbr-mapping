# Guatemala Fire Severity Mapping

Repository for mapping fire severity in Guatemala in collaboration with The Nature Conservancy and Conservation Data Labs.

## Requirements

This repo assumes you have already installed R, Python (or other distributions like Anaconda), and RStudio. If you have not installed these tools, please install them before proceeding.

- [R](https://cran.r-project.org/)
- [Python](https://www.python.org/)
- [RStudio Desktop](https://posit.co/download/rstudio-desktop/)

## Clone Repository

To start, clone this repository to your local machine. For instructions on cloning a repo, see this [link](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository). Alternatively, you can download this repo by selecting the "Download ZIP" option under the Code button.

## Initial Setup

The code in this repo is dependent on both R packages and Python libraries. Follow the below instructions to setup your machine after cloning.

**Note: these setup instructions only need to be run once when the repo is first cloned**

### Python

#### Create a Virtual Environment

In a terminal or command shell, navigate to the project directory on your local machine using `cd` or `chdir`. For example, on my machine the command would be `cd /c/Users/<my-username>/Documents/cdl-guatemala-dnbr-mapping`.

Once in the project directory, create a virtual environment by running the following commands:

```
python -m venv venv
```

#### Activate Virtual Environment

Still in the project directory, activate the virtual environment by running one of the following commands:

*Mac/Linux*

```
source venv/Scripts/activate
```

*Windows*

```
venv\Scripts\activate
```

#### Install Required Packages

Lastly, run the following command to install the dependencies for Python:

```
pip install -r requirements.txt
```
### R

In an R console, run the following command to install `reticulate`, a package that allows R and Python to work together. More info about `reticulate` can be found [here](https://rstudio.github.io/reticulate/index.html).

Additionally, install `renv` to manage the R packages.

```
install.packages("reticulate")
install.packages("renv")
library(renv)
```

#### Connect Reticulate to Python

Now we need to connect R and Python using `reticulate`. In an R console window, run the following command, replacing the `<path-to-python>` with the path to your virtual environment Python install.

```
reticulate::use_virtualenv("<path>/<to>/<your>/<venv>", required = TRUE)
```

For example, on my machine, I ran the command:

```
reticulate::use_virtualenv("C:/Users/Documents/cdl-guatemala-dnbr-mapping/venv", required = TRUE)
```

To test this was successful, run the following command in an R console:

```
reticulate::py_config()
```

If you see the path to your virtual environment python, you have successfully connected R and Python!

## Setting Up Google Earth Engine

This repo relies on Google Earth Engine and you will need an account (it's free) to use this code.

### Creating a Google Earth Engine Project

First you will need to create a Google Cloud Project and give it Earth Engine access. Here's the documentation from Google on setting that up (here)[https://developers.google.com/earth-engine/guides/access].

### Connecting Google Earth Engine to this Project

To confirm your local version of this project can connect to Google Earth Engine, run the following lines in a Python terminal, replacing "project" with the name of the project you created in the step above.

```
  ee.Authenticate()
  ee.Initialize(project)
```

## Regular Startup

Once you have setup the project following the instructions above once, the following steps will need to be taken each time you want to start up and use this project:

1. Open the `.Rproj` file
2. In a command prompt/terminal window, activate your Python virtual environment ([see instructions above](#activate-virtual-environment))

After running these two steps, your environment is ready to run scripts.

## Resources

https://spatialthoughts.com/2024/10/23/large-image-exports-gee/

