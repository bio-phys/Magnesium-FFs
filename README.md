# Magnesium-FFs

[Link](https://github.com/bio-phys/optimizedMgFFs) to parameters in SPC/E, TIP3P-fb, TIP4P/2005, TIP4P-Ew, and TIP4P-D.

[Link](https://github.com/bio-phys/MgFF_OPC) to parameters in OPC.

## Introduction
We have developed two sets of force field parameters for Magnesium Mg2+, `microMg` and `nanoMg`, for use in combination with the TIP3P water model.
Both optimized force fields simultaneously reproduce thermodynamic and structural properties of aqueous solutions (hydration free energy, radius of the first hydration shell, and coordination number of the first hydration shell). 

The parameter set `microMg` furthermore reproduces the experimental water exchange rate on the microsecond timescale, while `nanoMg` yields water exchange on the nanosecond timescale. 

Upon fine tuning of the Lorentz-Berthelot combination rules, additional thermodynamic and structural properties are reproduced (activity coefficient derivative, binding affinity, and distance towards the binding sites) for the interaction towards Chloride and RNA. 

Our optimized parameters aim to precisely capture the role of Magnesium in all-atom molecular dynamics simulations of biological processes including ion specific binding and ion binding kinetics.


## Quick start guide
Our parameters are optimized for the TIP3P water model.
The parameters are optimized for use with [Mamatkulov-Schwierz](https://github.com/bio-phys/Force-fields-for-metal-cations) (https://doi.org/10.1063/1.5017694) and parmBSC0chiOL3 RNA force fields (e.g. `amber14sb.ff`).
All parameter sets here are to be used with the Lorentz-Berthelot combination rule (otherwise modifications are required).
Note that we have chosen unique names for the optimized parameters to avoid errors in overwriting atom names:
* `mMg` - MG with water exchange as in experiment
* `nMg` - MG with accellerated water exchange

To get started: Replace the standard ion names in your `.gro` file by our unique names.
Modify the given topology file according to your system. The topology file includes the optimized force field parameters via `ffMg.itp` and `Mg.itp`


## Example 1: 0.5 molar MgCl2 using microMg

Folder example_MgCl2 contains all files for an MD simulation of 0.5 molar MgCl2 solution with GROMACS.
Initial coordinates are given in `MgCl2.gro`

To create a `.tpr` file for energy minimization type: 
```
gmx grompp -f MgCl2.mdp -c MgCl2.gro -p topol_MgCl2.top -maxwarn 27
```

(`maxwarn 27` is required as in the parameter file all scaled interactions towards all RNA atomtypes are explicitly listed, this is of cause not mandatory if no RNA is simulated)

## Example 2: add A-riboswitch with nanoMg

Folder example_1y26withMg contains all files for an MD simulation of the add A-riboswitch (PDB ID:1y26) with GROMACS.
Initial coordinates are given in `1y26withMg.gro`

To create a `.tpr` file for energy minimization type: 
```
gmx grompp -f 1y26withMg.mdp -c 1y26withMg.gro -p topol_1y26withMg.top -n index.ndx -maxwarn 27
```
(`maxwarn 27` is required as in the parameter file all scaled interactions towards all RNA atomtypes are explicitly listed)

## Citation
If you use our optimized parameters for Magnesium please refer to:
K. K. Grotz, S. Cruz-Leon, N. Schwierz (JCTC, 2021, https://pubs.acs.org/doi/10.1021/acs.jctc.0c01281)


Implementation has been tested by Kara K. Grotz.
USE AT YOUR OWN RISK!!
