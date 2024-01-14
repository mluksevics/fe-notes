---
weight: 2
title: "01 Design Flow"
---
# Design flow

## Overview of design flow

There is an idea that has stuck in my mind since I heard it from a
technical director during my first months at Buro Happold: "Calculation
write-up is a key deliverable".

Your model should tell a "story". Thinking of your design as a "story",
helps to systemize your actions and thinking.

### The sections of every good "story"

-   Geometry:
    -   Location of the considered element;
        - Is this an entire building? 
        - Or one single detail?
    -   Overall geometry;
        - What has been modelled? 
        - Where does it come from?
    -   Section sizes;
-   Materials:
    -   Steel / Timber / RC / Composite... combination?
    -   Linear/non-linear?
    -   What are the simplifications you are making and caused limitations?
-   Design assumptions - supports, hinges, stiffness modifications
-   Applied loads, load cases and combinations;
-   Type of analysis done, mesh properties;
-   Internal forces in elements;
-   Design of elements - checks according to code;

It is important to understand that this "story" is not dependent on
the software you use. In fact, I haven't come across a building
design where these sections wouldn't apply.

## What will your model do?

### Before you start modelling, ask yourself:

-   **What will your model do?** What will it be used for?
-   What is the goal you will achieve by getting the results?
-   What is the scope of the model?
    -   Is this a local model capturing a connection or floor slab?
    -   Is this an overall building model?

### Some examples of model types:

-   Overall model for stability system design;
-   Overall model to design columns;
-   Local model to design roof truss;
-   Local model to design a steel connection;
-   Local model to design an RC slab;

### More questions about overall building model

-   **Which elements should be safely designed by using this model?**\
    Columns? Stability system? Slabs? Transfer beams? \
    This is closely linked to the overall structural scheme assumptions of the building.
    Nevertheless, without this appreciation and strategy, you are set to
    waste a lot of time to create a model that does "everything" and
    "doesn't do anything well".

-   **What level of detail/precision you are supposed to deliver?**\
    Do you need to rapidly explore multiple options in the concept
    state?\
    Or do you need to minimize the section sizes as part of the redesign
    done by the contractor?\
    Remember that also the model (FE solver) running time will be longer
    for more complex models and this will restrict the assessment of
    many iterations of design.

## Dark age of technology

Technology develops quickly. The versions of programs we used 5
years ago are no longer used.

It is very likely that in some time of the future someone will want
to modify/refurbish the building you are designing.

Once, I had to open and make minor adjustments to a model of a
well-known tensile structure in London - the model was some 15+
years old. If there wouldn't be knowledge within the company and
software installation saved, then it is likely that would have
needed to remodel the entire structure and spend weeks on the simple
task.

-   Always note the version of the program used for analysis and/or
    design;
-   Save the installation files of used software along the project;
-   Export data and result reports in formats that have proven to
    survive over the past \~25 years: .pdf, .doc and .xls.

## Safety first!

With the new possibilities of the software (non-linear materials,
contact behaviour etc.) you will be tempted to model the structure in
more and more detail. However, remember, that your main goal is to
design a safe structure.

-   Don't worry about modelling the exact behaviour or structure;
-   **Do worry** about the safety of the structure -- always make
    modelling/design assumptions on the safe side!

This leads us to the next section about simplifications used in design using FEA.