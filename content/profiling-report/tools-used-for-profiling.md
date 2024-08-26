---
title: "Tools used for profiling"
date: 2024-08-20
categories:
- GSoC 2024
---

#### Tools Used

- cProfiler + snakeviz - Time profiler with filters and flamegraph
- scalene - Time + Memory line profiler
- memray - Memory profiler that uses flamegraph

#### Set up

Most of the profiling is done via CProfiler. Here is how you can get started with it: 

```
import cProfile, pstats
with cProfile.Profile() as pr:
    # Code to profile
    pass

stats = pstats.Stats(pr)
stats.sort_stats(pstats.SortKey.TIME)
stats.dump_stats(filename="file_name.prof")
```

You can then run your project normally and it will dump the stats in the file name provided in this case `file_name.prof`. 
In order to visualize this file, you need to first install snakeviz and then run it. Here is how you can do it: 

```
python -m pip install snakeviz
snakeviz file_name.prof
```

This will open a webpage with the profiled information.