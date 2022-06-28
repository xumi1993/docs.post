# Receiver functions

## Synthetic receiver functions (teleseismic body wave)

### 1D modelling
- [Raysum](https://home.cc.umanitoba.ca/~frederik/Software/): Ray-theoretical modelling of teleseismic waves in dipping, anisotropic structures   
    - [PyRaysum](https://paudetseis.github.io/pyraysum/): Teleseismic body wave modeling through stacks of (dipping/anisotropic) layers
    - [pyfwrd](https://github.com/NoisyLeon/pyfwrd): A forward modelling code for surface wave, receiver functions and shear wave splitting, given tilted hexagonal symmetric media
- [Telewavesim](https://paudetseis.github.io/Telewavesim/): Teleseismic body wave modeling through stacks of (submarine/anisotropic) layers
    - [RMATRIX](http://seis.karlov.mff.cuni.cz/software/sw3dcd22/rmatrix/rmatrix.htm) is invoked: Finds the R/T coefficient matrices for a stack of anisotropic layers.
- `trftn96` in [CPS330](http://www.eas.slu.edu/eqc/eqccps.html): Make a P-wave receiver function for a transverse isotropic model
- [RFTN](http://eqseis.geosc.psu.edu/cammon/HTML/RftnDocs/rftn01.html) C.J. Ammon's Code: An Overview of Receiver-Function Analysis

### 2D modelling
- [PSV Hybrid RF](https://github.com/Geolab-USTC/PSV_Hybrid_RF): Calculating synthetic RF in two-dimensional localized hetergeneous structures based on PSV Hybrid method (GRT-FD)

### 3D modolling
- [SPECFEM3D_Cartesian](https://specfem3d.readthedocs.io/en/latest/): Simulates seismic wave propagation at the local or regional scale and performs full waveform imaging (FWI) or adjoint tomography based upon the spectral-element method (SEM). The injection of teleseismic wavefield is avaliable with SEM-FK and AxisSEM method. See `COUPLE_WITH_INJECTION_TECHNIQUE` in `Par_file`
  - SEM-FK: Plane wavefield injection coupling with Cartesian SEM domain.
    Refer to {any}`../seismo/specfem3d/index` for usage.
    :::{admonition} Citation
    :class: seealso
    Tong, P., Komatitsch, D., Tseng, T.-L., Hung, S.-H., Chen, C.-W., Basini, P., and Liu, Q. (2014), A 3-D spectral-element and frequency-wave number hybrid method for high-resolution seismic array imaging, Geophys. Res. Lett., 41, 7025– 7034, [doi:10.1002/2014GL061644](https://doi.org/10.1002/2014GL061644).
    :::
  - [AxiSEM](https://seg.ethz.ch/software/axisem.html): 3-D seismic wavefields propagation in axisymmetric media
    :::{admonition} Citation
    :class: seealso

    T. Nissen-Meyer, M. van Driel, S. C. Staehler, K. Hosseini, S. Hempel, L. Auer, A. Colombi and A. Fournier: "AxiSEM: broadband 3-D seismic wavefields in axisymmetric media", Solid Earth, 5, 425-445, 2014 [doi:10.5194/se-5-425-2014](https://doi.org/10.5194/se-5-425-2014)
    :::

## Receiver function Process

### Python

- [Seispy](https://seispy.xumijian.me): Python Module for seismology and receiver functions
    - Batch calculation
    - GUI picking
    - H-k stacking
    - CCP stacking
    - Azimuth anisotropic estimation
    - Slant stacking
- [rf](https://rf.readthedocs.io/): Python framework for receiver function analysis.
    :::{admonition} Citation
    :class: seealso
    Tom Eulenfeld (2020), rf: Receiver function calculation in seismology, Journal of Open Source Software, 5(48), 1808, [doi:10.21105/joss.01808](https://doi.org/10.21105/joss.01808)
    :::
    - Batch calculation
    - CCP stacking
- [RfPy](https://paudetseis.github.io/rfpy/)
    - Gaussian weighted CCP stacking
    - H-k stacking
    - Back-azimuth harmonics 

### Matlab

- [Funclab](https://robporritt.wordpress.com/software/): Matlab based GUI for handling receiver functions
    :::{admonition} Citation
    :class: seealso
    Porritt, R. W. and Miller, M. S., (2018), Updates to FuncLab, a Matlab based GUI for handling receiver functions. Computers and Geoscience, 111, 260-271, [doi:10.1016/j.cageo.2017.11.022](https://doi.org/10.1016/j.cageo.2017.11.022)
    :::
- [SplitRFLab](https://github.com/xumi1993/SplitRFlab): A Matlab toolbox of processing receiver functions and shear wave splitting
    ```{admonition} Citation
    :class: seealso
    Xu M, Huang H, Huang Z, et al. SplitRFLab: A MATLAB GUI toolbox for receiver function analysis based on SplitLab[J]. Earthquake Science, 2016, 29(1): 17-26.
    ```
    - RF codes invoked from [processRFmatlab](https://github.com/iwbailey/processRFmatlab): Matlab functions and scripts for working with receiver functions

- [Crazyseismic](https://github.com/yucqSUSTech/Crazyseismic): A MATLAB GUI‐based software package for passive seismic data preprocessing
    :::{admonition} Citation
    :class: seealso
     Yu, C.Q., Zheng, Y.C., Shang, X.F. (2017), Crazyseismic: A MATLAB GUI-based software package for passive seismic data preprocessing, Seismol. Res. Lett., 88(2A), 410-415, [doi:10.1785/0220160207](https://doi.org/10.1785/0220160207)
    :::

### C/Fortran

- [CPS330](http://www.eas.slu.edu/eqc/eqccps.html): Collection of programs for calculating theorectical seismogram, receiver function, surface wave dispersion curve et al.
    :::{admonition} Citation
    :class: seealso
    Herrmann, R. B. (2013) Computer programs in seismology: An evolving tool for instruction and research, Seism. Res. Lettr. 84, 1081-1088, [doi:10.1785/0220110096](https://doi.org/10.1785/0220110096)
    :::
- [hk & ccp](http://www.eas.slu.edu/People/LZhu/home.html): Prof. Zhu Lupei's code
    - [{icon}`fas fa-download` hk1.3](http://www.eas.slu.edu/People/LZhu/downloads/hk1.3.tar): Receiver function package (deconvolution and H-k stacking)
    - [{icon}`fas fa-download` ccp1.0](http://www.eas.slu.edu/People/LZhu/downloads/ccp1.0.tar): Common-Conversion-Point (CCP) stacking of receiver functions
- [H-k-c](https://github.com/ljt-uiuc/H-k-c): Generalized H-k after harmonic correction on receiver functions
   ```{admonition} Citation
    :class: seealso
    Li, J., Song, X., Wang, P., & Zhu, L. (2019). A generalized H-k method with harmonic corrections on Ps and its crustal multiples in receiver functions. J. Geophys. Res. Solid Earth, 124(4), 3782-3801.
   ```


## Receiver function (joint) inversion

### Bayesian inversion
- [MC3deconv](https://github.com/akuhara/MC3deconv): Bayeisan inversion to recover Green's functions of receiver-side structures from teleseismic waveforms
    :::{admonition} Citation
    :class: seealso
    T. Akuhara, M. Bostock, A. Plourde, M. Shinohara (2019) Beyond Receiver Functions: Green's Function Estimation by Trans-Dimensional Inversion and Its Application to OBS Data, Journal of Geophysical Research: Solid Earth, [doi:10.1029/2018JB016499](https://doi.org/10.1029/2018JB016499)
    :::
- [BayHunter](https://jenndrei.github.io/BayHunter/): McMC transdimensional Bayesian inversion of surface wave dispersion and receiver functions
    :::{admonition} Citation
    :class: seealso
    Dreiling, Jennifer; Tilmann, Frederik (2019): BayHunter - McMC transdimensional Bayesian inversion of receiver functions and surface wave dispersion. GFZ Data Services. [doi:10.5880/GFZ.2.4.2019.001](http://doi.org/10.5880/GFZ.2.4.2019.001)
    :::
- [RfSurfHmc](https://github.com/nqdu/RfSurfHmc): Joint inversion of Receiver Function and Surface Wave Disperion by Hamilton Monte Carlo Method

### Gradient inversion
- [CPS330](http://www.eas.slu.edu/eqc/eqccps.html) Collection of programs for calculating theorectical seismogram, receiver function, surface wave dispersion curve et al.
    - `rftn96` for receiver function inversion
    - `joint96` for joint inversion with surface wave dispersion
