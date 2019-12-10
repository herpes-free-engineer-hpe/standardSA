Standard implementation of the Spalart-Allamaras model for compressible solvers.
OpenFOAM's implementation doesn't include the ft2 laminar suppression term,
which was reintroduced in this model.

Compile with `wmake libso` and reference to the `libstandardSA.so` library in
controlDict.

Description
-----------

Spalart-Allmaras one-eqn mixing-length model for incompressible and
compressible external flows.

Reference:

>   Spalart, P.R., & Allmaras, S.R. (1994).
>   A one-equation turbulence model for aerodynamic flows.
>   La Recherche Aerospatiale, 1, 5-21.


The model is implemented without the trip-term, but maintaining the ft2
term, considered as standard.

Extended according to:

>   Allmaras, S. R., Johnson, F. T., & Spalart, P. R. (2012).
>   Modifications and Clarifications for the Implementation of the
>   Spalart-Allmaras Turbulence Model.
>   ICCFD7-1902, 7th International Conference on Computational Fluid Dynamics,
>   Big Island, Hawaii, 9-13 July 2012.


using the optional flag *neg*

It is necessary to limit the Stilda generation term as the model generates
unphysical results if this term becomes negative which occurs for complex
flow.  Several approaches have been proposed to limit Stilda but it is not
clear which is the most appropriate.  Here the limiter proposed by Spalart
is implemented in which Stilda is clipped at Cs*Omega with the default value
of Cs = 0.3.

The default model coefficients are

    standardSACoeffs
    {
        Cb1         0.1355;
        Cb2         0.622;
        Cw2         0.3;
        Cw3         2.0;
        Cv1         7.1;
        Ct3         1.2;
        Ct4         0.5;
        Cn1         16.0;
        Cs          0.3;
        sigmaNut    0.66666;
        kappa       0.41;
    }
