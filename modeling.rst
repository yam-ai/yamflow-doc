********
Modeling
********

Introduction
============
The second swimlane in :numref:`yamflowchart` illustrates the Modeling
work stream. 
In this work stream, the data scientst explores the data sets, 
experiments various ML models with the data sets, 
optimizes the hyperparameters to get the desired results,
and finally codes the selected and turned ML model.

+--------------------------------+---------------------------------------------------------+-------------------+--------------------+
| Activity                       | Description                                             | Inputs            | Outputs            |
+================================+=========================================================+===================+====================+
| `Explore Data`_                | The available data sets are explored and the            | Raw or            | Suitable           |
|                                | suitable ones are prepared (in the Pipelining work      | cleaned data      | data set           |
|                                | stream for modeling the ML problem.                     |                   |                    |
+--------------------------------+---------------------------------------------------------+-------------------+--------------------+
| `Experiment Models`_           | Various ML models (e.g., neural network                 | Suitable          | Selected           |
|                                | architectures) are experimented using the data          | data set          | ML                 |
|                                | to select an effective model for the ML problem         |                   | model              |
+--------------------------------+---------------------------------------------------------+-------------------+--------------------+
| `Optimize Hyperparameters`_    | Hyperparameters are turned to test the selected         | Selected          | Finalized model &  |
|                                | model so that ML training can be efficiently performed. | ML model          | hyperparameters    |
+--------------------------------+---------------------------------------------------------+-------------------+--------------------+
| `Code Model`_                  | The finalized ML model is programmed for training       | Finalized model & | ML model coded for |
|                                | and inference. Application development may be           | hyperparameters   | training &         |
|                                | involved.                                               |                   | inference          |
+--------------------------------+---------------------------------------------------------+-------------------+--------------------+

.. _explore_data:

Explore Data
============

In this activity, the data scientist explores the data sets prepared 
in the Pipelining work stream and selects the suitable data sets 
for training and inference. 
Usually, the data scientist would use an interactive data science tool 
(also known as data science notebook) to explore the data sets.
If the suitable data sets are unavailable 
or incomplete or malformed or unclean, further data acquisition, cleansing, 
or  preprocessing work in the Pipelining work stream will be required.
The data scientist can also suggest how the suitable data sets should be 
prepared in the Pipelining work stream.

.. _experiment_model:

Experiment Models
=================

In this activity, the data scientist designs the ML model using the 
selected data sets. For example, he or she develops various ML models 
(e.g., neural network architectures), trains the models with a 
training data set, validates the models with the testing data set, and then
selects the suitable model based on the inference accuracy measures, such as 
`precision and recall <https://en.wikipedia.org/wiki/Precision_and_recall>`_.

.. _optimize_hyperparameters:

Optimize Hyperparameters
========================

In this activity, the data scientist tunes the 
`hyperparameters <https://en.wikipedia.org/wiki/Hyperparameter_optimization>`_ 
so that the model can be further optimized, for example, 
in terms of training speed and inference accurancy. 
Different ML algorithms may involve different sets of hyperparameters
(e.g., learning rate, model size, number of passes, regularization).
The data scientist may need to go back and forth between 
the  `Experiment Models`_ activity and the `Optimize Hyperparameters`_ activity
in order to define the optimal ML model.

.. _code_model:

Code Model
==========

After the ML model with the hyperparameters are defined, 
the ML model is programmed as training and inference applications. 
This activity may require various system development and 
infrastructure skills 
(e.g., Web API development, container packaging)
and is thus often performed by the data engineer or software engineer.
