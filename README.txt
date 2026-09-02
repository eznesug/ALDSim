Supplementary Code - ALDSim2.0 Kinetic Monte Carlo for ZnS ALD
========================================================================

This folder contains the source code and input files used to generate the
kinetic Monte Carlo (kMC) trajectories reported in the manuscript. The kMC
simulations were performed with the authors' own software ALDSim2.0, which is
built on the open-source SPPARKS parallel kMC framework. A software-copyright
registration has been filed for ALDSim2.0 (registration no. 2026SR0465717; please
insert the full number when available).

Contents
--------
src/
    Modified SPPARKS application and diagnostic files implementing the
    ZnS chemical model (application style ald/zns), together with the
    serial/MPI build scripts.
examples/ald-ZnS/
    input scripts (in_*.ald) and initial site data (data.ald) for each
    deposition temperature (300-500 K). The .ald dump files are simulation
    outputs and are not included.

Build
-----
From the src/ directory, compile the serial or MPI executable, e.g.

    bash build_serial.sh
    bash build_mpi.sh

or build with the standard SPPARKS Makefile.

Run
---
Each subdirectory under examples/ald-ZnS contains an input script for one
temperature. For example, to run the 300 K case:

    ./spk in_300.ald

The input script creates the ZnS surface, applies the pulse/purge sequence,
and writes the mass (QCM) and growth diagnostics.

Output
------
The diagnostic files report the number of atoms of each species as a function
of the ALD cycle, from which the growth per cycle (GPC) and the residual ethyl
(carbon) content are obtained. The full coordination-dependent event list and
parameter set are defined in the input scripts and in the reaction table of the
paper.

Notes
-----
The application implements the sulfur-based site and species set, the
coordination-number-dependent rate expressions with the steric-hindrance mask
function, and the pulse/purge pressure-switch that activates the DEZ and H2S
reactions during the appropriate stages of the ALD cycle.
