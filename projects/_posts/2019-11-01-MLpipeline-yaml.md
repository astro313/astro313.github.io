---
layout: post
title: "Automate ML Pipeline Using Configuration File"
date: 2019-11-01
---

## using PyYAML to automate ML pipeline

I have been writing some ML codes mainly for my simulation data (how I am using ML for my galaxy simulation data will be a separate post itself). Recently, I worked on a data challenge, where I incoporated some ML classification models. I decided to automate the process as part of the challenge -- so the 'deliverables' aren't just a bunch of scripts. 

I was given some raw data. I wrote some codes to pre-process the data, make plots to visualize the results, build multiple different ML models (depending on the user). Pointers to the input data and paths to output files are specified in a configuration file (config.yaml). The automation is essentially done by calling a main function in python that call each some scripts in sequence. 

At the moment, whether the use a parameter/configruation file is the best way to automate the ML pipeline remains unclear to me. Alternatives are possible, and I shall explore in the future (e.g., using [GNU Make]({% post_url 2019-11-11-packaging-ML-pipeline %})).