# IXO Liquidity Mechanism cadCAD Modelling

## Running the simulation

The main notebook is named `ixo.ipynb`.

When the notebook is run, a folder named `experiment_x/` is created for every parameter sweep. Within this folder are the outputs of the experiments, such as charts, pickles, and logs.

## Helper files

1. `bonding_curve_eq.py` - a set of bonding curve functions, from the BlockScience Augmented Bonding Curve model
2. `helpers.py` - a set of helper functions for processing data structures, such as the network graph or Pandas data frames

## Generating a PDF of notebook

To generate a PDF of the notebook, a Nix build file is included, run `nix-build pdf.nix` to generate a PDF document in the `result/` directory.

