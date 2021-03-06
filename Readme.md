Introduction
============

This package contains several helper functions for use in data manipulation, folder creation and viewing purposes. See examples of such functions below.

To install this package, run:

    if (!require("devtools")) install.packages("devtools")
    library(devtools)
    devtools::install_github("Nicktz/rmsfuns")
    library(rmsfuns)

build\_path
-----------

This function builds the entire folder path provided by the user. If the path does not exist, it builds it without error. It is effectively a user-friendly wrapper to the base function dir.create.

    library(rmsfuns)
    build_path("C:/Temp/data")

ViewXL
------

This function makes it easy to quickly view any R object or dataframe in excel. A random file is created in R's temporary folder location (see tempdir() to find your location). The excel file location can also be overridden using the FilePath command.

    library(rmsfuns)
    df <- data.frame(date = seq(as.Date("2012-01-01"),
                            as.Date("2015-08-18"),"day"), x = rnorm(1326, 10,2))
    ViewXL(df)

To clean the R temporary file folder (done periodically if using ViewXL often - especially with large excel files), use CleanTempFolder:

    library(rmsfuns)
    CleanTempFolder()

PromptAsTime
------------

To change R's prompt to reflect the time, use the PromptAsTime function. This can be used as a simple means of timing long calculations without using sys.time() commands. This can be very useful if running, e.g., many functions overnight, and later viewing the time taken on multiple calculations.

To set the timer on, type:

    PromptAsTime(TRUE)

The time for each command will now be shown in Rstudio's prompt.

To set the prompt timer off, type:

    PromptAsTime(FALSE)

load\_pkg
---------

This function loads a vector of packages into R, and installs the package if it has not yet been installed.

    load_pkg(c("ggplot2", "dplyr"))
