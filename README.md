Standard implementation of the Spalart-Allamaras model for compressible solvers.
OpenFOAM's implementation doesn't include the ft2 trip-term, which was
reintroduced in this model.

Compile with `wmake libso` and reference to the `libstandardSA.so` library in
controlDict.
