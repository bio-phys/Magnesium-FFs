# Magnesium-FFs

## Introduction
******************
We have developed two sets of force field parameters for Magnesium Mg2+, microMg and nanoMg, for use in combination with the TIP3P water model.
Both optimized force fields simultaneously reproduce thermodynamic and structural properties of aqueous solutions (hydration free energy, radius of the first hydration shell, and coordination number of the first hydration shell). 

The parameter set microMg furthermore reproduces the experimental water exchange rate on the microsecond timescale, while nanoMg yields water exchange on the nanosecond timescale. 

Upon fine tuning of the Lorentz-Berthelot combination rules, additional thermodynamic and structural properties are reproduced (activity coefficient derivative, binding affinity, and distance towards the binding sites) for the interaction towards Chorid and RNA. 

Our optimized parameters aim to precisely capture the role of Magnesium in all-atom molecular dynamics simulations of biological processes including ion specific binding and ion binding kinetics.


## Quick start guide
******************
Our parameters are optimized for the TIP3P water model.
The parameters are optimized for use with parmBSC0chiOL3 RNA force fields (e.g. amber14sb.ff).
All parameter sets here are to be used with the Lorentz-Berthelot combination rule (otherwise modifications are required).
Note that we have chosen unique names for the optimized parameters to avoid errors in overwriting atom names:
* mMg - MG (water exchange as in experiment)
* nMg - MG (accellerated water exchange)

To get started: Replace the standard ion names in your .gro file by our unique names.
Modify the given topology file according to your system. The topology file includes the optimized force field parameters via ffMg.itp and Mg.itp


## Example: 0.5 molar MgCl2
******************
Folder contains all files for an MD simulation of 0.5 molar MgCl2 solution with GROMACS.
Initial coordinates are given in out.gro.
To create a .tpr file for energy minimization type: gmx grompp -f mdout.mdp -c out.gro -p topol.top

## Citation
******************
If you use our optimized parameters for Magnesium please refer to:
K. K. Grotz, S. Cruz-Leon, N. Schwierz (unpublished)


Implementation has been tested by Kara K. Grotz.
USE AT YOUR OWN RISK!!
