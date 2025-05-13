# Benchmarks

The benchmark files are defined at `xad/benchmarks` and the benchmarking script is defined at `xad/scripts`.

## Benchmark Suite

...


## Benchmark Script

The benchmark script has arguments:

```bash
./scripts/benchmark.sh <run_type: 'benchmark' | 'reference'> [<local: bool=false>] <test1> [<test2> ... <testN>]"
```

The `run_type` tells the script whether we're running for the reference (from main) or for our benchmark (from some
other branch). The `local` parameter is used to configure paths. If the script is running from a GitHub Actions container, this should
be set to `true`. The last arguments are the test names, as the name of directories directly in `xad/benchmarks`.


To correctly run the benchmarks, this directory structure should be followed:

```
root
  ↳ main
      ↳ ...
        benchmarks
        scripts
        ...
  ↳ xad
      ↳ ...
        benchmarks
        scripts
        ...
```

First, run the script in `reference` mode from the `main` directory. This will generate a
`reference.json` report.
Then, run the script in `benchmark` mode from the `xad` repository. This will generate a
`benchmark.json` report. It will then use the report from the other run to make a table,
`benchmark_results.md`. For tabulation and further analysis, it will also create a 
report, `benchmark_results.json`. These files can be found in `.../build/benchmarks`.