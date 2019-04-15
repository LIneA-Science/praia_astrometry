# PRAIA

PRAIA is the acronym for Platform for Reduction of Astronomical Images Automatically.

According to the author:
"PRAIA performs high precision differential photometry and astrometry on digitized images (CCD frames, Schmidt plate surveys, etc). The package main characteristics are automation, accuracy and processing speed. Written in FORTRAN 77, it can run in scripts and interact with any visualization and analysis software. PRAIA is in cope with the ever growing amount of observational data available from private and public sources, including data mining and next generation fast telescope all sky surveys, like SDSS, Pan-STARRS and others. PRAIA was officially assigned as the astrometric supporting tool for participants in the GAIA-FUNSSO activities and will be freely available for the astronomical community."

src: https://www.researchgate.net/publication/258559018_PRAIA_-_Platform_for_Reduction_of_Astronomical_Images_Automatically

This repository contains the `Dockerfile` used to build a docker image for the PRAIA_astrometry application.

### How to build the image

 git clone git@github.com:LIneA-Science/praia_astrometry.git
 cd praia_astrometry
 docker build -t praia .

### How to commit and push

Create a container before this.

 ```sh
 docker login
 docker commit <container_id> linea/praia:v20_09>     # e.g: v20_09
 docker tag <image_id> linea/praia:v20_09             # the id of the image created before
 docker push linea/praia:v20_09  
 ```