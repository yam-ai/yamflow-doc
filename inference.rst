*********
Inference
*********

Introduction
============
The fourth swimlane in :numref:`yamflowchart` illustrates
the Inference work stream.
In this work stream, the inference application is developed and deployed.
When the ML model is updated,
the inference application will load the model from the registry.
Finally, the inference application serves the updated model.

+----------------------------------+---------------------------------------------------------+-------------------+--------------------+
| Activity                         | Description                                             | Inputs            | Outputs            |
+==================================+=========================================================+===================+====================+
| `Develop Inference Application`_ | The inference application is developed using the coded  | Coded model       | Inference          | 
|                                  | ML model from the :doc:`modeling` work stream           |                   | app                |
+----------------------------------+---------------------------------------------------------+-------------------+--------------------+
| `Deploy Inference Application`_  | The developed inference application is deployed to the  | Developed         | Deployed           |
|                                  | server infrastructure.                                  | inference         | inference          |
|                                  |                                                         | app               | app                |
+----------------------------------+---------------------------------------------------------+-------------------+--------------------+
| `Update Model`_                  | The inference application loads the updated ML model    | Deployed          | Deployed inference |
|                                  | from the registry.                                      | inference         | app loaded         |
|                                  |                                                         | app &             | with updated model |
|                                  |                                                         | updated model     |                    |
+----------------------------------+---------------------------------------------------------+-------------------+--------------------+
| `Serve Model`_                   | The inferene application serves the loaded ML model.    | Inference inputs  | Inference outputs  |
|                                  | The inference inputs are fed from the :doc:`pipelining` | & deployed        |                    |
|                                  | work stream. The                                        | inference app     |                    |
|                                  |                                                         | loaded with       |                    |
|                                  |                                                         | updated model     |                    |
+----------------------------------+---------------------------------------------------------+-------------------+--------------------+

.. _develop_inference_application:

Develop Inference Application
=============================

The software engineer designs and implements the inferene application
that runs the coded ML model. The softwre engineer designs
the application based on the business requirements.
For example, the application may be designed to process the
inference input file by batch or provide RESTful APIs to
infer a message stream.

.. _deploy_inference_application:

Deploy Inference Application
============================

The inference application is deployed to the server infrastructure
on-premises or in the cloud.
The deployment can be done manually or automated with
`Infrastructure as Code <https://en.wikipedia.org/wiki/Infrastructure_as_code>`_.

.. _update_model:

Update Model
=============

The inference application loads the ML model from the registry.
When the ML model is updated in the :doc:`training` work stream,
the inference application will be triggered to load the updated
model automatically.

.. _serve_model:

Serve Model
===========

After the inference applicaiton has loaded the ML model,
the application processes the inference inputs from the
:doc:`pipelining` work stream and produces the inference outputs.
The inference outputs will be regularly fed to the
:doc:`pipelining` work stream for validation.
Some inference outputs can be selected to prepare the
training data for re-training in the future.
