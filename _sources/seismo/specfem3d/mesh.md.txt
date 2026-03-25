# Rules of meshes in Specfem3D
For built-in mesh generator, we can modify `DATA/meshfem3D_files/Mesh_Par_file` to define regions, meshes and materials.

## Define coordinates
First we define limits of `X`, `Y` and `Z` directory.
```
LATITUDE_MIN                    = -20000.0
LATITUDE_MAX                    = 20000.0
LONGITUDE_MIN                   = 0.0
LONGITUDE_MAX                   = 120000.0
DEPTH_BLOCK_KM                  = 120.0
UTM_PROJECTION_ZONE             = 11
SUPPRESS_UTM_PROJECTION         = .true.
```
- `LATITUDE` represents `Y` directory.
- `LONGITUDE` represents `X` directory.
- `DEPTH_BLOCK_KM` defines maximum depth of the SEM domain in km.

:::{note}

When `SUPPRESS_UTM_PROJECTION` is set to `.false.`, the `UTM_PROJECTION_ZONE` is activated. The map of UTM zone can be referred as following. In this case, the `LATITUDE` and `LONGITUDE` are true latitude and longitude in degree.

:::

:::{figure} ../../_static/utmworld.gif
:align: center
[UTM Grid Zones of the World](https://www.dmap.co.uk/utmworld.htm)
:::

## Set elements and materials

### Number of elements
```
# number of elements at the surface along edges of the mesh at the surface
# (must be 8 * multiple of NPROC below if mesh is not regular and contains mesh doublings)
# (must be multiple of NPROC below if mesh is regular)
NEX_XI                          = 24
NEX_ETA                         = 8

NPROC_XI                        = 2
NPROC_ETA                       = 2
```

- `NEX_XI`: Number of elements along `X` directory.
- `NEX_ETA`: Number of elements along `Y` directory.
- `NPROC_XI` and `NPROC_ETA` represent number of MPI processors along xi and eta, respectively. The `NPROC` in the `Par_file` should be `NPROC_XI` * `NPROC_ETA`.

:::{note}
If `USE_REGULAR_MESH` is set to `.true.`, number of elements must be multiple of `NPROC`. Otherwise, number of elements must be multiple of 8. 
:::

### Interface and elements along depth directory

Set number of layers in first effective line. For each interface, we set parameters of interface file as

```
# SUPPRESS_UTM_PROJECTION  NXI  NETA LONG_MIN   LAT_MIN    SPACING_XI SPACING_ETA
.true.                     2    2    0.0        -20000.0   120000.0   40000.0
interf_1.dat
```
- The interface denotes the top of layer.
- Number of `interf_1.dat` must be `NXI`*`NETA`.

Then set up number of elements for each layer `NZ`.

```{todo}
Need update for cases of multi layers 
```

### Materials of elements

Define properties of materials as

```
# #material_id  #rho  #vp  #vs  #Q_Kappa  #Q_mu  #anisotropy_flag  #domain_id
1  2920  6500  3850  9999. 9999.  0  2
2  3423  8060  4530  9999. 9999.  0  2
```

Then assign materials to elements

```
NREGIONS                        = 2
# define the different regions of the model as :
#NEX_XI_BEGIN  #NEX_XI_END  #NEX_ETA_BEGIN  #NEX_ETA_END  #NZ_BEGIN #NZ_END  #material_id
1            24              1             8            18           25          1
1            24              1             8            1            17          2
```

## Avoid numerical dispersion
The size of meshes is closely correlated to stability of numerical solution in forward modelling. There are **two** key points to avoid numerical dispersion.

### 1. Wavelength of seismograms

The size of the elements must be smaller than the minimum possible wavelength in the region.

:::{math}
L &< {\lambda}_{min} \\
&< \frac{v_{min}}{f}
:::

In the setting above, we assume the {math}`v_{min}=6500\ m/s`, where the {math}`v_{min}` is the Vp of the first layer. The wavelength is defined by the frequency of source time function. In the SEM-FK mode, the frequency {math}`f=2.0\ Hz` is defined in `FKMODEL` with `f0`. So the maximum size of element should be less than {math}`3.25\ km`.

If the size of each element bas been determined as 5 km. the maximum frequency should be less than {math}`\frac{v_{min}}{L}=1.3\ Hz`.

#### Gaussian Factor and cutoff frequency
A Gaussian low pass filter can be expressed as in frequency domain

:::{math}
G(\omega) = e^{-\frac{{\omega}^2}{4{\alpha}^2}}

\omega = 2{\pi}f
:::

where {math}`f` is the physical frequency, {math}`\alpha` is the Gaussian Factor. As the {cite:t}`monteiller2021validity` suggestion, the so called cut-off frequency can be defined as that corresponding to that the energy of the source spectrum drops to values lower than 1 per cent of the maximum.Therefore, the normalized cutoff frequency is

:::{math}
f_{cut} = \frac{\alpha}{\pi}\sqrt{-\ln(0.01)}
:::

the correspondence between Gaussian Factor and cutoff frequency is

```{figure} ./figures/gaussf.png
:name: Gaussian factor against cut-off frequency
```

### 2. Sampling rate

As a introduction to [choosing the time step](https://specfem3d.readthedocs.io/en/latest/04_creating_databases/#choosing-the-time-step-dt) in user manual, the condition of time step `DT` in `Par_file` is

:::{math}
\Delta t<C \mathrm{min}_{\Omega}(\frac{h}{v})
:::

where {math}`C` is the so-called Courant number and {math}`\Omega` denotes the model volume. The distance {math}`h=\frac{L}{N_{GLL}}` depends on the mesh element size and the number of GLL points (defaults to 5). The Courant numbers empirically chosen {math}`C\approx0.3`.  

:::{note}
>If you used the mesher `xmeshfem3D` to generate your mesh, you should set the value suggested in `OUTPUT_FILES/output_mesher.txt file`, which is created after the mesher completed.

```
 ***
 *** Maximum suggested time step for simulation =    0.04837248
 ***
```
:::