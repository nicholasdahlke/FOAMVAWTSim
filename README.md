# VAWT Simulation
## Cleanup
Remove all the old generated mesh files
```rm -r constant/polyMesh```
```rm -r processor*```
```rm -r 2```

## Run
If it has not been done before, generate the feature edge mesh
```surfaceFeatureExtract```

Generate the background block mesh
```blockMesh```

Decompose the case for parallel processing
```decomposePar```

Run the case in parallel on 24 threads
```mpirun --use-hwthread-cpus -np 24 snappyHexMesh -parallel```

Reconstruct the mesh
```reconstructParMesh -mergeTol 1e-06 -latestTime```


