# Polarizable Kremer-Grest
This repository contains an example input script for studying ionomer melts with coarse-grained simulations. The charged species include polarization at the level of Drude oscillators, where the charge on each bead is divided between a fixed core and the remaininng charge spatially fluctuates relative to the core.

*Author* - Chris Balzer

See more details in publication [Balzer and Frischknecht, Macromolecule, 55 (2022)](https://doi.org/10.1021/acs.macromol.2c01608). If you find this repository helpful, please cite our paper.

## LAMMPS Info
All of the simulations were run on CPU. The systems studied in the paper were quite large (400 chains), so over total 100 CPU threads were used for each simulation (MPI across nodes). For the example here, the system has 50 chains and can be run in a reasonable time on a few CPU threads. The LAMMPS packages necessary are `KSPACE`,`MOLECULE`,`DRUDE`,`RIGID`.

## Contents of ``example`` folder
- ``lammps.in``: Main LAMMPS input file
- ``params.data``: Forcefield parameters for pairs and bonds. It's convenient to have pairs defined for all combinations of Drude and counterion models so that the same one can be loaded (that's why there are 9 atom types)
- ``system.data``: Initial configuration of system (again note the 9 components but not all are used)

## Description of example system
50 chains with spacer length N=7 and relative dielectric constant of 4. The polarizabiltiy is the _high_ case from the paper (see ``params.data``). The polarizability is only used in LAMMPS for the Thole screening function. The charge of the Drude particles is determined beforehand using the value of the polarizability.
