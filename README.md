# Kinetic Monte Carlo Study of Atomic Layer Deposition of Zinc Sulfide

Supplementary source code and input files for the manuscript

> **Kinetic Monte Carlo Study of Atomic Layer Deposition Process of Zinc Sulfide**
> Senze Gu, Chengyu Yin, Junyang Hong, Yongjian Weng, Chunyang Zhu, Lina Xu, Hongping Xiao, Guoyong Fang*

This repository contains the source code and input files used to generate the
kinetic Monte Carlo (kMC) trajectories reported in the above manuscript. The
simulations were performed with the authors' own multiscale ALD simulation
platform **ALDSim**, built on the open-source
[SPPARKS](https://spparks.sandia.gov/) parallel kMC framework. ALDSim has been
registered with the China Copyright Protection Center (registration no.
2026SR0404643).

## Contents

- `src/` — modified SPPARKS application and diagnostic files implementing the
  ZnS chemical model (application style `ald/zns`), together with the
  serial/MPI build scripts.
- `examples/ald-ZnS/` — input scripts (`in_*.ald`) and initial site data
  (`data.ald`) for each deposition temperature (300–500 K), together with the
  serial/MPI SLURM job scripts.
- `aldsim-python/` — ALDSim Python desktop edition: a PyQt5-based graphical
  interface with 2D/3D visualization for lattice-based ALD kMC simulations.

## Build

From the `src/` directory:

```bash
bash build_serial.sh   # serial executable: spk
bash build_mpi.sh      # MPI executable: spk_mpi
```

## Run

Each subdirectory of `examples/ald-ZnS/` contains an input script for one
temperature. For the 300 K case:

```bash
./spk in_300.ald
```

The input scripts create the ZnS surface, apply the DEZ/H₂S pulse–purge
sequence, and write the mass (QCM) and growth diagnostics. The diagnostic files
report the number of atoms of each species as a function of the ALD cycle, from
which the growth per cycle (GPC) and the residual ethyl (carbon) content are
obtained.

## Notes

The application implements the sulfur-based site and species set, the
coordination-number-dependent rate expressions with the steric-hindrance mask
function, and the pulse/purge pressure-switch that activates the DEZ and H₂S
reactions during the appropriate stages of the ALD cycle. The complete
coordination-dependent event list and parameter set are defined in the input
scripts and in the reaction table of the manuscript (Table S1 of the Supporting
Information).

## Citation

If you use this code, please cite the manuscript and ALDSim.

---

See `README.txt` for the original notes.
