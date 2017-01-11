```

Adjust OS Memory: most of OS take 4-8 GB of memory

Workload factor:  it’s a factor that signifies an interplay between input data size and DFS block size.

The number of splits in map task can depend on them:

Number of splits (maps)=(dataset size)/(block size)

The number of splits can be larger, if you set mapreduce.job.maps larger than (dataset size)/(block size) . That might be needed, for example, if you have a lot of small input size (smaller than block size). 

Setting of mapreduce.job.maps which is smaller than the number of splits has no effect (serves just as a lower bound)


```