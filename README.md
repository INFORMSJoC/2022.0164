[![INFORMS Journal on Computing Logo](https://INFORMSJoC.github.io/logos/INFORMS_Journal_on_Computing_Header.jpg)](https://pubsonline.informs.org/journal/ijoc)

# DiversiTree: A New Method to Efficiently Compute Diverse Sets of Near-Optimal Solutions to Mixed-Integer Optimization Problems

This archive is distributed in association with the [INFORMS Journal on
Computing](https://pubsonline.informs.org/journal/ijoc) under the [MIT License](LICENSE).

The software and data in this repository are a snapshot of the software and data
that were used in the research reported on in the paper (https://doi.org/10.1287/ijoc.2019.0000) by Izuwa Ahanor, Hugh Medal and Andrew Trapp.
The snapshot is based on 
[this SHA](https://github.com/izuwaa/Diversitree/commit/a9f459bc73bc2eba8956623aad7d79cf16ea0c08) 
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
  url =           {https://github.com/INFORMSJoC/2019.0000},
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
- `SCIP`: A critical dependency for DiversiTree, which stands for "Solving Constraint Integer Programs".
- `nodeType`: The type of nodes considered during the optimization process. The values 0 and 1 represent different node types.
- `alphaValue`: A list of alpha values used within the branch-and-bound framework.
- `optimizationProblem`: The name of the optimization problem file.
- `requestedNumberSolutions`: The desired number of near-optimal solutions to be computed.
- `percentNearOptimal`: The percentage of near-optimal solutions in the generated solution set.
- `Verbosity`: The level of verbosity during the execution of DiversiTree.
- `beta`: A parameter with a range of values.
- `prioritizedParam`: The parameter that is set at a given value and prioritized during the optimization process.
- `solutioncutoff`: The solution cutoff value used during optimization.
- `depthcutoff`: The depth cutoff value used during optimization.
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
