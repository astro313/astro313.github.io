---
layout: post
title: "Automate ML Pipeline Using GNU Make"
date: 2019-11-11
---

As I mentioned in [my other post](2019-11-01-MLpipeline-yaml.md), I automated some ML codes by writing a main function in python that executes various scripts in sequence to preprocess the data, visualize the data, train ML models, evalute model, make predictions, etc. Alternatively, we can use GNU Make to call these scripts, which in contrast to the python main function approach, this way we can remove all existing data using the good-old "clean" rule, but also, we'd be able to test the codes as part of the "all" rule. This way, we wouldn't have to call e.g., `pytest`. 

Perhaps the GNU Make approach is a bit easier to implement, but probably just a touch. Perhaps, the advantage of using GNU Make approach would be more apparent if we need to do other things in the command line/shell rather than just running some python scripts. For instance, if we want to reserve nodes on a super computer, then one would have to call some job scheduler (e.g., SLURM)