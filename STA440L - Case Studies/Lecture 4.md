# Case Study 1

## Intro

This data comes from a Ph.D. Student at a university in Madagascar. His work is under a grant that is attempting to take an inventory of all life on Earth and use that information to build a more sustainable future (e.g., with alternative food sources). The data source is extremely high-dimensional (in the hundreds of millions of variables). As many as 80-90% of Madagascar species are endemic (i.e., they occur nowhere else).

## The Problem

Crickets have been a staple of diets around the world for centuries. Cricket cultivation can be done at a small scale by local farmers and are great sources of protein and income. We seek to find which species of crickets are best cultivated in various regions of Madagascar.

We are receiving the first stage of the experiment: there are four species that have the most promise for farming. We are looking at their life history trajectory (hatching, mortality rate, growth rate, etc.) to find which species of crickets are best to grow at various temperature/humidity conditions.

We are also interested in generation time, which measures how quickly a cricket goes from being born to laying an egg of its own. This could drastically impact the rate at which crickets can be farmed.

## The Experiment

A single cricket starts off in a box with unlimited food. As time advances, various metrics are measured in a controlled setting. So far, we have seen that humidity has great effect to survival rate. Cotton balls are placed in the enclosure to see when eggs are hatched (they lay eggs on cotton balls for some reason).

## Our Task

### EDA

First we explore the existing data. We want to look for trends in the data, but **especially red flags in experiment design**.