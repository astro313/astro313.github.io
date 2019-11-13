---
layout: post
title: "Tools for Building ML Pipeline"
date: 2019-11-14
---

## Docker, travis, GNU make, Configuration file
I am picking up Docker, travis, GNU make, but find myself wondering about the following - how to incoportate all of these together to build a pipeline / how do they complement one another in building a pipeline?

These are my questions for now, which will be answered promptly (and updated here) as I bug some of my friends. 

### A Configuration File to Define Paths
One part of automating a ML pipeline would be to have paths and options/keyword arguments specified in a configuration file, which would be read directly when the python scripts are called. 

### Using GNU Make
When we want to automate the ML pipeline, we could write a GNU Make script to do "clean", "download data", "test", "preprocess data", "plot", "train", "predict", etc, where reading in the config file would be part of it. 

### Write a Python main Function
Alternatively, one could write a python script as the main function to execute these .py files in place of GNU make. This way, I also know how to make travis work with purely .py files, but I have not gotten used to thinking about how I would integrate travis with GNU make (in case I would like to automate the process using GNU make instead of a python main function).

### Docker with GNU Make?
But as the concept of Docker comes into place, I got confused. In particular, do people typically use Docker with GNU make? If so, how would the structure of this setup look like? Would one set up "Docker" as a rule in the Makefile? which would call `docker build`, `docker run`? If so, how would we implement a test rule - I guess the test scripts would need to be executed within the Docker container instead of as a separate rule in the Makefile?

### Docker with travis?
What about Docker and travis? For people using Docker, how would they use travis to do continuous integration that test the code? What would the .travis.yml file look like? I guess there won't be any `before_install`, `install`, etc? But then one would need to ensure the environment used to build the Docker image is identical to that of travis. Hmm...