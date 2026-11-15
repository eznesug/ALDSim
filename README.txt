ALDSim - Multiscale Kinetic Monte Carlo Platform for Atomic Layer Deposition
===========================================================================

ALDSim (原子层沉积多尺度模拟软件) V1.0 is a lattice-based kinetic Monte
Carlo (KMC) simulation platform for atomic layer deposition (ALD), built on the
open-source SPPARKS parallel kMC framework. A software-copyright registration
has been filed for ALDSim V1.0 (registration no. 2026SR0404643, copyright
holder: Wenzhou University).

This folder ships the ZnS DEZ/H2S ALD model as one demonstration application of
the ALDSim platform; the kMC trajectories reported in the associated manuscript
were generated with this model.

Contents
--------
src/
    Modified SPPARKS application and diagnostic files implementing the
    ZnS chemical model (application style ald/zns), together with the
    serial/MPI build scripts.
aldsim-python/
    ALDSim Python desktop edition: PyQt5 graphical interface with 2D/3D
    visualization for lattice-based ALD kMC simulations.
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
