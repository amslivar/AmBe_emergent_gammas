# AmBe_emergent_gammas

Simulation of AmBe emergent gammas (based on emergent gammas simulation code for AmLi by J. Busenitz and R. Sazzad). 

Prerequisite: Geant 4.10.04.p02 and ROOT 5.34/07 (later versions are ok)

Author: Mariia Fedkevych, mariia.fedkevych@gmail.com

1. Download and unpack the AmBe_emergent_gammas.tar.gz archive, e.g. run "tar -xf AmBe_emergent_gammas.tar.gz" in Linux terminal
2. Source setup scripts for Geant4, e.g.
   
```bash
source /usr/local/geant4.10.04.p02/bin/geant4.sh
source /usr/local/geant4.10.04.p02/share/Geant4-10.4.2/geant4make/geant4make.sh
```
3. Go to the AmBe_emergent_gammas folder and run "cmake -DGeant4_DIR=/path/to/local/geant4VersionInstalled/lib64/Geant4.xxxx/ path/to/extracted/source/directory", e.g.

```bash
cmake -DGeant4_DIR=/usr/local/geant4.10.04.p02/lib64/Geant4-10.4.2/ .
```

5. Compile with `make` (it will create an executable named "capsule_emissionV2")
6. Prepare an HEPEvt format generator file for AmBe gamma spectrum (from `am241be.spectrum`) which will be read by capsule_emissionV2: 
    - make an executable of am241be.cc, e.g. run
      ```bash
      g++ am241be.cc -o am241be.exe
      ```
    - run the executable with the number of events to be generated and the output file name "generator.data", e.g.
      ```bash
      ./am241be.exe 10000000 > generator.data
      ```
7. The simulations can be executed by running
  ```bash
   ./capsule_emissionV2 AmBe.mac
   ```
10. The output root file "outcapsule.root" containing energy distributions of primary and detected gammas will be generated within the same folder (the filename and path can be changed in src/ExN03RunAction.cc file). 
11. If you didn't comment out the visualization options in AmBe.mac, it will generate .wrl file in the same folder. 
12. Example .wrl files which visualize the geometry is contained within "geometry_vis_example" subfolder
