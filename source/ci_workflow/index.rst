:title: CI Workflow

CI Workflow
===========

The workflow of Continuous Integration is the following:

.. image:: /_static/images/ci_workflow.png
    :class: img-responsive img-thumbnail

Inside each repository there are the following files:

* ``Dockerfile``: It describes how to build the container image from source code.
* ``captain.yml``: It describes the preparation steps, the test executions and the container namespace of the repository.

For more info about Captain see the `here <https://github.com/harbur/captain>`_.

During CI for each commit push on the repository a build is triggered that executes ``captain push``. This will execute the following phases:

* ``Preparation stage``: Executions such as compilation of the code can be done here.
* ``Build stage``: The build of the Dockerfile generates the container image.
* ``Post stage``: Executions of post code can be done here.
* ``Test stage``: Test execution commands can be added here, in order to test the quality of the generated image.
* ``Push stage``: Once the image has been tested properly and no errors were found the image is now pushed to the remote repository.

If any stage fails the build will stop and the image will not be pushed to the remote repository, giving the guaranty that the pushed images are test-failure free.
