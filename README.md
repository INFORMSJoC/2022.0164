[![INFORMS Journal on Computing Logo](https://INFORMSJoC.github.io/logos/INFORMS_Journal_on_Computing_Header.jpg)](https://pubsonline.informs.org/journal/ijoc)

# [DiversiTree: A New Method to Efficiently Compute Diverse Sets of Near-Optimal Solutions to Mixed-Integer Optimization Problems](https://doi.org/10.1287/ijoc.2022.0164)

This archive is distributed in association with the [INFORMS Journal on
Computing](https://pubsonline.informs.org/journal/ijoc) under the [MIT License](LICENSE).

The software and data in this repository are a snapshot of the software and data
that were used in the research reported on in the paper (https://doi.org/10.1287/ijoc.2019.0000) by Izuwa Ahanor, Hugh Medal and Andrew Trapp.
The snapshot is based on 
[this SHA](https://github.com/izuwaa/2022.0164/7514eb90d8f560797178c6141be9f531342b8fd8) 
in the development repository. 

**Important: This code is being developed on an on-going basis at 
https://github.com/izuwaa/Diversitree. Please go there if you would like to
get a more recent version or would like support**

## Cite

To cite the contents of this repository, please cite both the paper and this repo, using their respective DOIs.

https://doi.org/10.1287/ijoc.2019.0000

https://doi.org/10.1287/ijoc.2019.0000.cd

Below is the BibTex for citing this snapshot of the respoitory.

```
@article{ahanor2022diversitree,
  author =        {Ahanor, Izuwa and Medal, Hugh and Trapp, Andrew C},
  publisher =     {INFORMS Journal on Computing},
  title =         {{DiversiTree: Computing Diverse Sets of Near-Optimal Solutions to Mixed-Integer Optimization Problems}},
  year =          {2022},
  doi =           {10.1287/ijoc.2019.0000.cd},
  url =           {https://github.com/izuwaa/2022.0164},
}  
```


# DiversiTree

DiversiTree is a method for efficiently computing diverse sets of near-optimal solutions to mixed-integer optimization problems. This repository contains the implementation of DiversiTree, along with instructions on how to run the code.

## Dependencies

- GCC (6.3.0 or compatible version)
- CMake
- SCIP (required for mixed-integer optimization)

## Installation

Before installing DiversiTree, make sure to have the following dependencies installed:

1. GCC:
   - Install GCC version 6.3.0 or a compatible version.

2. CMake:
   - Install CMake using your package manager or from the official website: https://cmake.org/download/

3. SCIP:
   - DiversiTree depends on SCIP for mixed-integer optimization.
   - Install SCIP by following the instructions provided in the SCIP documentation: [SCIP Installation Guide](https://www.scipopt.org/doc-7.0.3/html/install.php)

## Getting Started

These instructions will guide you on how to set up and run DiversiTree on your system.

### Installation

1. Clone the repository and navigate to the Diversitree base directory:
```
git clone https://github.com/izuwaa/Diversitree.git

cd Diversitree

```

2. Configure and build the project:

```
cmake -Bbuild -H. -DSCIP_DIR=/scip/directory/installDir/lib/cmake/scip -DGMP_INCLUDE_DIR=/other/important/includes

```


## Usage

To run DiversiTree, follow these steps:

1. Change to the DiversiTree directory:

```
cd /path/to/DiversiTree
```


2. Execute the DiversiTree executable, providing the necessary input files e.g.:

```
/path/to/DiversiTree/build/diversitree input_file.txt problemOptions , solverParams.txt solverOptions
```


- `input_file.txt`: The input file containing the mixed-integer optimization problem and parameters. Can be named anything; The naming content in the files must however be strictly followed
- `problemOptions`: Additional options for the problem. Keyword - Indicates that the preceding file (input_file.txt) contains problemOptions.
- `solverParams.txt`: Parameters for the solver. Can be named anything; The naming content in the files must however be strictly followed
- `solverOptions`: Options for the solver. Keyword - Indicates that the preceding file (solverParams.txt) contains solverOptions.


## Input File Format

The `input_file.txt` contains the following details and definitions:

- `solver`: The solver to be used by Diversitree. Options are `SCIP, GAMS`.
- `nodeType`: The node selection rule to use. Options are `0, 1, 2, 3, 4 or 5'. Where 0 - "DiversiTree", 1 - "bfs", 2 - "dfs", 3 - "uct", 4 - "hybridestim", and 5 - "breadthfirst". 
- `alphaValue`: Alpha (α) ∈ [0, 1] is a parameter that trades off the bound of node i against its diversity score. You can provide a single alpha value or several values (separated by a comma). The code runs through the alpha values and provides a diversity score for each provided value. An alpha value of 1 means that Diversitree considers only diversity - selecting the node that gives the maximum diversity.
- `optimizationProblem`: The name(s) of the optimization problem file(s) to solve. If multiple problems are provided at the same time, separate them with a comma. The file should be located in the "misfiles" folder with the exact name provided here.
- `requestedNumberSolutions`: The desired number of near-optimal solutions to be computed. Can be a single requested number of solutions or multiple solutions separated by a comma.
- `percentNearOptimal`: How close to the optimal should the generated solutions be? You can provide a single percent value e.g 0.03, 0.1.
- `Verbosity`: The level of verbosity during the execution of DiversiTree.
- `beta`: Beta (β) ∈ [0, 1] controls the depth of the node in the Diversitree node selection rule. A β value of 1 means that the node selection rule works like depth first search and selects the next node to process based on the depth. You can provide a single beta value or several values (separated by a comma). The code runs through the beta values and provides a diversity score for each provided value.
- `prioritizedParam`: options `beta, alpha`. This parameter that is first set and set at a given value and prioritized during the optimization process.
- `solutioncutoff`: The solution cutoff parameter, that is, the number of solutions that must be accumulated before diversity is considered in node selection.
- `depthcutoff`: The depth cutoff parameter, that is, the depth that must be reached before diversity is considered in the node selection.
- `computeDiversity`: A flag to indicate whether to compute the diversities of captured solutions (0) or write the captured solutions to a CSV file (1).
- `computeDiversityFromCsv`: A flag to indicate whether a CSV file with solutions is available (1) or not (0). If available, only the diversity of the k most diverse solutions will be computed, where k is represented by the parameter `requestedNumberSolutions`.
- `csvFile`: The path to the CSV file containing solutions.
- `pMostDiverseSolutions`: The number of most diverse solutions to consider.



## Ongoing Development

This code is being developed on an on-going basis at the author's
[Github site](https://github.com/izuwaa/Diversitree).

## Support

For support in using this software, submit an
[issue](https://github.com/izuwaa/Diversitree/issues/new).
