---
weight: 9
title: "08 Analysis"
---
# Static Analysis

This may be the most sophisticated part from theoretical standpoint,
however, from user's=engineer's perspective there is relatively small
number of choices -- there is not a lot you can do wrong here. 

Firstly -- understand whether your model requires non-linear analysis.
It could be that program automatically switches to non-linear solver as
soon as you introduce any model features that require non-linear
analysis (both Autodesk Robot and Dlubal RFEM will do this).

Regarding **linear analysis.** Linear analysis assume that deformations
are very small, and geometry of deformed structure does not affect
internal forces in elements. It also assumes, that stress increase in
elements (both bars and surfaces) have no effect on stiffness of these
elements.

**Non-linear analysis** will mean that there will be
multiple iterations of your calculation. There are two
causes that "trigger" use of non-linear analysis.
-   **Geometry**. Consideration of deflected shape in calculations.
    -   Tension-only or Compression-only elements;
    -   Contact supports, or any restraint that can work in one-direction
        only (it may be rotation allowed in one direction as well);
    -   Although this will not be automatically identified by software, you
        should always use non-linear analysis if you have elements that have
        **large forces in both axial and transverse** (i.e. shear) directions.
    -   "Large deformation" analysis should be also be used for **thin surfaces** 
        with relatively large permissible deformations. One example would be 
        design of glass panes where panes might be as thin as 3mm and a typical 
        deflection limit would be L/100.
-   **Material**. Consideration that material does not have linear
    stress-strain curve. E.g. consideration of plastic deformations.
    -   if you want to consider plastic behaviour of steel or cracking
        and/or creep of concrete, you must use non-linear material and
        therefore non-linear analysis.
    -   You should be able to select which stress is used to trigger the
        modification of stiffness. The reasonable typical choice is "von
        Mises" stress as this will account for normal stress in both
        directions and shear stress.

The following are the **basic steps done in non-linear analysis**:
1.  Calculate single linear analysis run;
2.  Update calculation model with deformed structure from previous run;
3.  Update calculation model with new material properties (e.g., if
    yield stress has been reached);
4.  Re-calculate single linear analysis run using updated geometry and
    stiffness;
5.  Compare last two runs. If the difference is small enough, the
    analysis has "converged". If not -- keep cycling -- go to step one.
6.  Sometimes steps 1 to 5 gets repeated for multiple load increments,
    allowing a better convergence. Say applying one third of the load ,
    repeating steps 1 to 5 until convergence and then adding second
    third.. then remaining third of the load.

**Further reading on analysis** types. I believe these are relevant even if you use another analysis software:
-  [Dlubal RFEM knowledge base](https://www.dlubal.com/en/support-and-learning/support/knowledge-base/001504)
-   [Autodesk Robot user guide](https://knowledge.autodesk.com/support/robot-structural-analysis-products/learn-explore/caas/CloudHelp/cloudhelp/2017/ENU/RSAPRO-UsersGuide/files/GUID-FB3C86D3-0E30-43A6-82D6-6C50F429FA0D-htm.html)

There may be options to choose between **32bit and 64bit** solvers. And
single thread vs. **multithreaded**. These won't (at least -- shouldn't)
have any effect on analysis results. Of course, 64bit multithreaded
solver theoretically should be the fastest.

Analysis requires computer to **read/write a lot of data**.
Although generally I strongly support that all data is kept on server,
for analysis this can significantly slow down process. Therefore, if the
model is large, I suggest you copy the model on your machine, run calculations on you local hard (SSD) drive and then copy back on the server.