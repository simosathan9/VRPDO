# VRPDO

Benchmark datasets and analytical solutions for the **Vehicle Routing Problem with Delivery Options (VRPDO)**.

This repository hosts the two established VRPDO benchmark sets used to evaluate our algorithm, together with the solutions produced by our method on each instance.

## Repository structure

```
.
├── Tilk_et_al_2021/         # Small-scale benchmarks (Tilk et al., 2021)
├── Dumez_et_al_2021/        # Large-scale benchmarks (Dumez et al., 2021)
├── Analytical_Solutions/    # Solutions produced by our algorithm
│   ├── Tilk_et_al_2021/     # Solutions for the first dataset
│   └── Dumez_et_al_2021/    # Solutions for the second dataset
└── README.md
```

## Datasets

### First dataset — small-scale (Tilk et al., 2021)

120 instances organised in 12 classes following a 2 × 2 × 3 design:

- **Service flexibility:** `U` (two options per request) or `V` (1.5 options on average)
- **Scale:** 25 or 50 requests
- **Time-window tightness:** `small`, `medium`, or `large`

File naming: `{U|V}_{25|50}{small|medium|large}_{1..10}.txt` (10 instances per class).

Original source: https://logistik.bwl.uni-mainz.de/research/benchmarks

### Second dataset — large-scale (Dumez et al., 2021)

Purpose-built instances covering a 3 × 4 design:

- **Configuration:** `U`, `V`, or `UBC` (high-capacity)
- **Scale:** 50, 100, 200, or 400 customers

File naming: `{U|V|UBC}_{50|100|200|400}_{1..10}.txt` (10 instances per class).

> **Note:** The `V_400_*` and `UBC_400_*` instances (20 files) are not yet included in this repository. They can be obtained from the original source referenced by Dumez et al. (2021).

## Instance file format

Each file describes a single VRPDO instance: depot, customers, delivery options (individual and shared locations), time windows, demands, service and preparation times, and vehicle capacity. The format follows the conventions of the original benchmark sets cited above.

## Analytical solutions

The `Analytical_Solutions/` folder contains the solutions produced by our algorithm for the instances in both benchmark datasets, organised to mirror the data structure:

- `Analytical_Solutions/Tilk_et_al_2021/` — one subfolder per instance class (e.g. `U_25small/`, `V_50large/`), each holding 10 solution files following the naming `{class}_{1..10}greedy.txt`.
- `Analytical_Solutions/Dumez_et_al_2021/` — one subfolder per instance class (e.g. `U_100/`, `UBC_50/`, `V_50/`), each holding 10 solution files following the naming `{class}_{1..10}greedy.txt`.

Each solution file reports the feasibility flag, restart/repetition counters, the total cost, the number of routes, priority-fulfilment statistics, and the detailed route plan (location, option, customer for every visit). Reported costs match the values listed in Appendix A of the accompanying manuscript.

## References

- Tilk, C., Olkis, K., & Irnich, S. (2021). *The last-mile vehicle routing problem with delivery options.* OR Spectrum.
- Dumez, D., Lehuédé, F., & Péton, O. (2021). *A large neighborhood search approach to the vehicle routing problem with delivery options.* Transportation Research Part B.

## License

The code and solutions in this repository are released under the MIT License (see `LICENSE`).

The benchmark instances under `Tilk_et_al_2021/` and `Dumez_et_al_2021/` are redistributed for research convenience and remain subject to the terms of their original sources (see references above). Please cite the original papers when using these instances.
