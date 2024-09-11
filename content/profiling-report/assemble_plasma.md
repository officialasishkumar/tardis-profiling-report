---
title: "Profile assemble_plasma function"
date: 2024-09-11
categories:
- GSoC 2024
---

The `assemble_plasma` function in total takes 2.773 seconds when ran on [tardis_example.yml](https://raw.githubusercontent.com/tardis-sn/tardis/master/docs/tardis_example.yml) without GPU. Here is the overall breakdown according to the cumulative time the other function takes: 

The average of 5 iterations was taken to write these profiling results. 

| Function | Time (seconds) | Calls |
|----------|----------------|-------|
| [plasma/assembly/legacy_assembly/assemble_plasma](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/assembly/legacy_assembly.py#L5) | 2.773 | 1 |
| [plasma/assembly/base/@assemble](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/assembly/base.py#L587) | 2.675 | 1 |
| [plasma/base/BasePlasma/@__init__](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/plasma/base.py#L26) | 2.668 | 2 |
| [plasma/base/@update](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/base.py#L183) | 2.663 | 2 |
| [plasma/properties/base/@update](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/properties/base.py#L98) | 2.659 | 44 |
| [opacities/macro_atom/base/@calculate](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/opacities/macro_atom/base.py#L250) | 1.384 | 2 |
| [opacities/macro_atom/base/TransitionProbabilities/@_calculate_transition_probability](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/base.py#L110) | 1.381 | 2 |
| [plasma/properties/radiative_properties/BetaSobolev/@calculate](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/plasma/properties/radiative_properties.py#L133) | 1.179 | 2 |
| [io/atom_data/base/AtomData/@prepare_atom_data](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/io/atom_data/base.py#L401) | 0.08669 | 1 |
| [io/atom_data/base/AtomData/@prepare_macro_atom_data](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/io/atom_data/base.py#L538) | 0.05516 | 1 |
|[plasma/properties/radiative_properties/StimulatedEmissionFactor/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/properties/radiative_properties.py#L70) | 0.03859 | 2 |
