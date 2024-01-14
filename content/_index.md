---
weight: 1
title: "Engineer's notes"
---

# Introduction

This is a set of notes, tips and tricks about the **design** of
buildings using finite element analysis. These are notes about the
questions I had on a path from a being a fresh graduate to a
senior engineer. Notes are written in the summer of 2020.

## Topics covered at a glance

-   What are the simplifications of material behaviour commonly used in
    FE models of built structures;
-   What toolbox do you have for creating a model and how to choose the
    parameters of model components;
-   How to apply loads and systematically create load combinations;
-   How to prepare/check model for analysis and how to choose mesh size;
-   Options for analysis types of your structure;
-   How to systematically look for and "catch" instabilities that appear
    during calculation;
-   Ways and workarounds to tackle challenges specific to RC and steel modelling and design;

These should give guidance to answer questions such as:

-   Should I model a pinned or fixed connection there?
-   How can I account for cracking and creep in concrete?
-   Software is telling me that the model is unstable.. where should
    start looking for a problem?
-   My slab model shows very high reinforcement above columns? Is there
    an error in my model?
-   What mesh size should I choose?

## Focus on the design

These notes are not about "How to use software X or software Y".
Although I have mostly used Autodesk Robot Structural Analysis or Dlubal
RFEM (examples are created using this software) and designed according to Eurocodes, I believe that **many approaches
explained here apply to any FEA software and design code**.

There is a gap in the available literature between \"knowing FE
software\", \"knowing FE fundamentals (maths)\" and "understanding
structural behaviour". And these are my notes trying to fill that \"gap\".

I have focused on **concrete, steel and timber** structures and left out
advanced topics and areas that I am not familiar with. Seismic design, dynamics or calculations of 3D solid FE elements are outside of the scope of these notes.

## Target audience

The target audience for these notes are **students and graduate
engineers** progressing towards chartership/certification.\
You should familiar with the basics of structural analysis -
what does "hinge" or "support" mean, and how do statically
determinate/indeterminate systems differ. Experience with any FE
software would is helpful, but not a necessity. I believe that
anyone can pick up a new software in a matter of few weeks if only the
person knows exactly what she wants to model, what assumptions to use,
what are limitations and what results to calculate.

In many cases, the answer to a question is "it depends" and there might not be one
single "correct" way of doing things. I'll make the most of the freedom
this format gives - I won't suppress my **engineering judgment**. You
or your line manager might disagree with my advice. However, even if you
go through the thought process to explain your disagreement, I will have
achieved the goal - you will have taken into account the modelling
consideration in question.