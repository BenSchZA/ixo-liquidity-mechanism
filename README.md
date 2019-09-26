# IXO Liquidity Mechanism cadCAD Modelling

**Objective**

Determine if there is a feasible mechanism to tie the reserve of the market maker mechanism with the reserve of the brokerage mechanism, to maintain the peg stability during the period needed to bootstrap the system. Acknowledging the discussed assumptions, incentive mechanisms, and actors, in the system - the ultimate objective is to ensure actors are incentivized to supply their assets into the system in exchange for utility so that the system can be bootstrapped effectively.

**Sprint 1 Scope**

1. Customize and parameterize the existing augmented bonding curve model developed by BlockScience
2. Determine the most suitable mechanism for tying the two reserves together (using the Kyber network and Uniswap mechanisms as inspiration)
3. Determine what parameters we have available to stabilize the market maker peg (initial assumption - use the reserve ratio, and possible exit taxation to prime this mechanism)
4. Determine if the mechanism is theoretically feasible

**Resources**

1. Augmented bonding curve hatch_sim notebook:  [https://github.com/BlockScience/conviction/blob/master/hatch_sim.ipynb](https://github.com/BlockScience/conviction/blob/master/hatch_sim.ipynb)
2. Kyber network reserve types: [https://developer.kyber.network/docs/Reserves-Types/](https://developer.kyber.network/docs/Reserves-Types/)

## Running the simulation

The main notebook is named `ixo.ipynb`.

When the notebook is run, a folder named `experiment_x/` is created for every parameter sweep. Within this folder are the outputs of the experiments, such as charts, pickles, and logs.

## Helper files

1. `bonding_curve_eq.py` - a set of bonding curve functions, from the BlockScience Augmented Bonding Curve model
2. `helpers.py` - a set of helper functions for processing data structures, such as the network graph or Pandas data frames

## Generating a PDF of notebook

To generate a PDF of the notebook, a Nix build file is included, run `nix-build pdf.nix` to generate a PDF document in the `result/` directory.

