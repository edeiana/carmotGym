# CARMOT Gym

This repository is designed to test CARMOT on well established benchmark suites.
This repository also includes the evaluation materials for the CARMOT CGO 2023 paper: "Program State Element Characterization".

## Artifact

This artifact generates four sets of results that correspond to the main results of the paper.
The first set of result corresponds to the black and red speedup bars of Figure 6.
The second set is the CARMOT overhead (red bar) in the OpenMP use case of Figure 7.
The third set is the CARMOT overhead (red bar) in the C++ Smart Pointer use case of Figure 10.
The fourth set is the CARMOT overhead (red bar) in the STATS use case of Figure 11.
Adding SPEC CPU2017 to each set of results is optional.

### Prerequisites 

The artifact is available as a docker image.
The artifact will generate the results when invoking the script ```./bin/carmot_minimal```.
The results set that is generated depends on the envionment variables set (see below).

We open sourced [CARMOT](https://github.com/edeiana/carmot.git).
We also open sourced the [infrastructure](https://github.com/edeiana/wholeprogram_benchmarks.git) we built to evaluate CARMOT on several benchmark suites (e.g., NAS, PARSEC3, SPEC CPU 2017).
This artifact will download everything is needed by cloning the open-sourced repositories.
This means the script ``bin/carmot_minimal`` will clone the open sourced git repositories (from GitHub) that are not included within the docker image.
So please make sure to have a network connection when you run the artifact.

### Experiments and results

After loading and running the docker image carmot.tar interactively as follows:
$ docker load < carmot.tar
$ docker run --rm -it carmot /bin/bash

The entry point to generate all four sets of results is the script /bin/carmot_minimal.
It must be invoked as follows with no arguments:
$ ./bin/carmot_minimal

Additionally, the user can control how many times each data point is executed by setting the environment variable CARMOT_NUM_RUNS to an integer value.
For example to generate each data point 5 times the user will invoke bin/carmot_minimal as follows:
$ export CARMOT_NUM_RUNS=5 ; ./bin/carmot_minimal

