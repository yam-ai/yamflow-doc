*******
YamFlow
*******

.. toctree::
   :maxdepth: 2
   :caption: Contents
   :hidden:

   pipelining.rst
   modeling.rst
   training.rst
   inference.rst

Introduction
============

YamFlow proposes a reference workflow for machine learning (ML).
This reference workflow is aimed to provide a canonical taxonomy for 
practitioners to understand and communicate the activity and data flows
typically involved in a ML process. In addition, YamFlow also serves
as the baseline for `YAM.AI <https://www.yam.ai>`_ to architect a 
programming framework for coding interoperable and composable ML tasks.

YamFlow Overview
================

:numref:`yamflowchart` shows the flowchart of YamFlow, which specifies
the overall process of a typical ML implementation in the design time and run time. 
Although the actual processes of different ML implementations may vary, 
the activity sequences and data flows should largely resemble YamFlow.

.. _yamflowchart:
.. figure:: _static/images/yamflowchart.svg
   
   YamFlow Chart.

YamFlow consists of the following work streams:

- :doc:`pipelining` specifies the work stream for building the data pipelines
  for ML modeling, training, and inference.
- :doc:`modeling` specifies the work stream for exploring the data, and 
  design and code the ML model.
- :doc:`training` specifies the work stream for training the coded model.
- :doc:`inference` specifies the work stream for deploying the inference application
  and serve the trained model.






