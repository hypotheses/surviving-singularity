.. highlightlang:: rest

.. _instance-services:

Singularity Container Instances Service
=======================================

From Singularity version 2.4 onwards, you can cleanly, reliably, and safely run services in a container.

For the example here, we will start ``nginx`` service inside the container instance. First, we will need to put the command that we want to run in a script.::

  %startscript
  service nginx start

Start the Instance
------------------

With the ``%startscript`` included in the singularity ``nginx.simg`` image. We can start the ``nginx`` service with::
  
                [command]        [image]    [name of instance]
  $ singularity instance.start   nginx.img  web

Check the Running Instance
--------------------------

After start up the service instance, you can check which instances are running using::

  $ singularity instance.list
  INSTANCE NAME    PID      CONTAINER IMAGE
  web              790      /home/mibauer/nginx.img
  
Multiple instances from the same image can be started as well.

Mount Host Folder (Bind Mount)
------------------------------

For example, if you wish to capture the output of the web1 container instance which is placed at /output/ inside the container you could do::

  $ singularity instance.start -B output/dir/outside/:/output/ nginx.img  web1
  
Connect to the Running Instance
-------------------------------

::

  $ singularity instance.stop web1

Stop the Running Instance
-------------------------

::
  
  $ singularity instance.stop \*
  $ singularity instance.stop -a
  
Reference
^^^^^^^^^

`Singularity: Running Services <http://singularity.lbl.gov/docs-instances>`