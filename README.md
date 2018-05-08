# Dohmen-Janssen-and-Hanes-2002
SedWaveFoam case setup for sheet flow under non-breaking waves (Dohmen-Janssen and Hanes, 2002)

### How to Simulate
* (1) FoamClearPolyMesh
* (2) blockMesh
* (3) snappyHexMesh -overwrite (If you want to skip the mesh refinement near the sediment pit, you can ignore this part)
* (4) go to 0 folder and make non-org files
cp -r alpha.water.org alpha.water
cp -r alpha.org alpha
cp -r gamma.org gamma
* (5) setWaveField (to fill the water, in default waves2Foam searches alpha.water and U)
* (6) copy U to Ub & alpha.water to alpha1 (SedWaveFoam uses alpha1)
cp -r U Ub
cp -r alpha.water alpha
* (7) funkySetFields -time 0 (to fill up the sediment and remove that portion in alpha1)
* (8) SedWaveRANSDEVFoam (you can make the parallel if you want)
