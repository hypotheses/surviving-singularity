.. highlightlang:: rest

.. _workflow:

Singularity workflow
====================

Create a Container
------------------

There are two ways to create a container 1) as a regular folder 2) as a disk image ``.simg``

1. as a regular folder within your specified directory

  ``sudo singularity build --sandbox ubuntu/ docker://ubuntu``
    
  with this option you can use ``tree -L 1 ubuntu`` to list the content of the current sandbox directly

2. as a disk image

  ``sudo singularity build --writable ubuntu.img docker://ubuntu``
  
  For this option, you will get a single ``ubuntu.img``, as a single container file. 

Customize the Container
-----------------------

i.e. installed the required packages, library, software -- 

1. as a regular folder

  ``sudo singularity shell ubuntu``

2. as a disk image

  ``sudo singularity shell --writable ubuntu.img``

Building the container image
----------------------------
build into a squashfs image::

 sudo singularity build ubuntu.simg ubuntu/
 sudo singularity build ubuntu.simg docker://ubuntu
 
This will clean up the image and only keep the differences from docker://ubuntu 

Reference
^^^^^^^^^^
- `Singularity Doc Flow <http://singularity.lbl.gov/docs-flow>`