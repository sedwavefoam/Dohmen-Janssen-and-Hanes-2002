# Dohmen-Janssen-and-Hanes-2002
SedWaveFoam case setup for sheet flow under non-breaking waves 
(details of physical experiment refer to Dohmen-Janssen and Hanes, 2002, JGR: Oceans, https://doi.org/10.1029/2001JC001045)
Modeling paper is published in JGR: Oceans (Kim et al., 2018, https://doi.org/10.1029/2018JC013930)

### How to Simulate
* (1) foamClearPolyMesh
* (2) blockMesh
* (3) snappyHexMesh -overwrite (If you want to skip the mesh refinement near the sediment pit, you can ignore this part)
* (4) extrudeMesh (This is to remove the redundant spanwise grids as an outcome of snappyHex)
* (5) go to 0 folder and make non-org files <br />
cp -r alpha.water.org alpha.water <br />
cp -r alpha.org alpha <br />
cp -r gamma.org gamma <br />
* (6) setWaveField (to fill the water, in default waves2Foam searches alpha.water and U)
* (7) copy U to Ub & alpha.water to alpha1 (SedWaveFoam uses alpha1) <br />
cp -r U Ub <br />
cp -r alpha.water alpha1 <br />
* (8) funkySetFields -time 0 (to fill up the sediment and remove that portion in alpha1)
* (9) SedWaveRANSDEVFoam (you can make the parallel if you want)
