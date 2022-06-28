# Receiver Function Forward simulation with Specfem3D_FWATR

:::{attention}
The Specfem3D_FWATR is under developing, so it has not been open accessed.
:::

## Preparation

For RF simulation, we invoked SEM-FK with plane wave injected to compute RFs, So parameter files are same as Specfem3D and SEM-FK, but an additional parameter file is required for RF calculation. 

### Common configures
- `DATA/Par_file`
- `DATA/meshfem3D_files`
- `DATA/CMTSOLUTION`

:::{note}
The `DATA/CMTSOLUTION` must exist but its parameters will not work.
:::
### Exclusive configures
- `src_rec/sources_setXX.dat`: Map of source set `XX` and event id `YY`. The first field is read to define `YY`.
- `src_rec/FKmodel_YY.dat`
- `src_rec/STATION_YY.dat`
- `fwat_params/FWAT.PAR`: 4 parameters are required for RF calculation, Others are the same as FWAT.
    - `RF_TSHIFT`: Time shift before P
    - `NUM_FILTER`: Number of Gaussian filters applied on RFs.
    - `F0`: Array of Gaussian factors
    - `MAXIT`: Maximum iterations
    - `MINDERR`: Minimum residuals

### Meshes and Parameters

{any}`./mesh` has introduced how to create meshes and database, but there are still some key points need be highlighted.

- Coupling between FK and SEM domain: for high frequency simulation, the abrupt changes of adjacent materials result in wavefield scattering. Thus a taper zone is necessary between FK and SEM, which involved a smooth transition both in velocity and interface topography.

    :::{note}
    - Taper zones are need to be set both along X and Y axis. 
    - The distance between first (last) station and the taper zone should be less than first Fresnel zone radius in effective depth.
    :::

- Coordinates of initial wavefront: if `ORIGIN_WAVEFRONT` is set, the initial wavefront should be out of the SEM domain. We can set up it to 4 bottom corner with different back-azimuth.


## Run simulation

### Create database

```
sed -i "/LOCAL_PATH                      =/c\LOCAL_PATH                      = ./OUTPUT_FILES/DATABASES_MPI" DATA/Par_file
sed -i "/LOCAL_PATH                      =/c\LOCAL_PATH                      = ./OUTPUT_FILES/DATABASES_MPI" DATA/meshfem3D_files/Mesh_Par_file

mpirun -np 4 ./bin/xmeshfem3D
mpirun -np 4 ./bin/xgenerate_databases
```

### Go forward simulation
```
mpirun -np 4 ./bin/xfwat0_forward_data M00 setXX rf
```

RFs will be saved into `data/YY` with SAC format as `knetwk.kstnm.kcmpnm.rf.sac`