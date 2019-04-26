# PRAIA

PRAIA is the acronym for Platform for Reduction of Astronomical Images Automatically.

According to the author:
"PRAIA performs high precision differential photometry and astrometry on digitized images (CCD frames, Schmidt plate surveys, etc). The package main characteristics are automation, accuracy and processing speed. Written in FORTRAN 77, it can run in scripts and interact with any visualization and analysis software. PRAIA is in cope with the ever growing amount of observational data available from private and public sources, including data mining and next generation fast telescope all sky surveys, like SDSS, Pan-STARRS and others. PRAIA was officially assigned as the astrometric supporting tool for participants in the GAIA-FUNSSO activities and will be freely available for the astronomical community."

src: https://www.researchgate.net/publication/258559018_PRAIA_-_Platform_for_Reduction_of_Astronomical_Images_Automatically

This repository contains the `Dockerfile` used to build a docker image for the PRAIA_astrometry application.

### How to build the image

```sh
 git clone git@github.com:LIneA-Science/praia_astrometry.git
 cd praia_astrometry
 docker build -t praia .
```

### How to commit and push

Create a container before this.

 ```sh
 docker login
 docker commit <container_id> linea/praia:v20_09>     # e.g: v20_09
 docker tag <image_id> linea/praia:v20_09             # the id of the image created before
 docker push linea/praia:v20_09  
 ```

How to run PRAIA

 ```sh
 docker run -it --name teste -v $PWD:/data -v /archive:/archive linea/praia:v30_06
 docker exec teste sh -c '/app/PRAIA_astrometry_30_06 < /data/PRAIA_astrometry_30_06_10.dat'
 ```

OBS: 
 - Assuming you're connected to the LIneA's environment.
 - On /app dir create symlinks to /data/PRAIA_astrometry_30_06_10.dat, /data/output and to the image file .fits. Whithout those the execution will thow an erro like this:

 ```sh
 Proccessing field     1 of     1: file = D00374550_z_c06_r2262p01_immasked.fits                                                                                                                
 Reached end of fits file. Exiting.

 Identifing and measuring objects. Please wait ...

 Program received signal SIGSEGV: Segmentation fault - invalid memory reference.

 Backtrace for this error:
 #0  0x7fecca7924f5 in ???
 #1  0x7fecca791af9 in ???
 #2  0x7fecca94d801 in ???
 Segmentation fault (core dumped)
 /app # read escape sequence

 ```
