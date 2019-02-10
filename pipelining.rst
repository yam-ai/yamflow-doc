**********
Pipelining
**********

Introduction
============
The first swimlane in :numref:`yamflowchart` illustrates the Pipelining
work stream. 
In this stream, the data engineer prepares the data sets for 
ML modeling, training, and inference. The activities are summarized in 
the following table.

+--------------------------------+-----------------------------------------------------+--------------+--------------+
| Activity                       | Description                                         | Inputs       | Outputs      |
+================================+=====================================================+==============+==============+
| `Acquire Data`_                | The necessary raw data from the data sources        | Various data | Raw data     |
|                                | (e.g., databases, edge devices) are aggregated      | sources      |              |
|                                | for ML modeling, training, and inference.           |              |              |
+--------------------------------+-----------------------------------------------------+--------------+--------------+
| `Clean Data`_                  | The raw data are cleaned so that the data quality   | Raw data     | Cleaned data |
|                                | is sufficient for labeling or preprocessing.        |              |              |
+--------------------------------+-----------------------------------------------------+--------------+--------------+
| `Label Data`_                  | Data points are labeled with expected inference     | Cleaned data | Labeled data |
|                                | outputs. Manual labeling may be necessary.          |              |              |
+--------------------------------+-----------------------------------------------------+--------------+--------------+
| `Preprocess Inference Inputs`_ | The data are transformed to the specific format     | Cleaned data | Inference    |
|                                | required for input to the inference application     |              | inputs       |
+--------------------------------+-----------------------------------------------------+--------------+--------------+
| `Preprocess Training Data`_    | The data sets are transformed to the specific file  | Labeled data | Training     |
|                                | format required by the ML library for training.     |              | data         |
+--------------------------------+-----------------------------------------------------+--------------+--------------+
| `Validate Inference Outputs`_  | The actual inference outputs are compared against   | Actual       | Selected     |
|                                | the expected outputs, which can be a manual         | inference    | outputs for  |
|                                | process. Inaccurate outputs can be selected for     | outputs      | relabeling   |        
|                                | relabeling to continously train and improve the ML  |              |              |
|                                | model in the future.                                |              |              |
+--------------------------------+-----------------------------------------------------+--------------+--------------+

.. _acquire_data:

Acquire Data
============

In this activity, the necessary raw data sets are acquired for ML modeling, training, 
and inference.
Data integration may be involved in generating ML data points that 
cover data fields from multiple data sources. Traditional 
`Extract, Transform, Load (ETL) <https://en.wikipedia.org/wiki/Extract,_transform,_load>`_
tools and 
`Enterprise Service Bus (ESB) <https://en.wikipedia.org/wiki/ESB>`_ 
may be used for simplifying data acquisition and integration.
Raw data often come in a variety of forms and thus
are commonly stored in data files or a database with 
a `schemaless <https://en.wikipedia.org/wiki/NoSQL>`_ or 
`columnar <https://en.wikipedia.org/wiki/Column-oriented_DBMS>`_ structure.

.. _clean_data:

Clean Data
==========

In this activity, the quality of the data sets is improved up to the standard 
required for the downstream ML. 
Through data cleansing, the raw data are cleaned
so that the resultant data for ML are as valid, accurate, complete, consistent, 
and uniform as expected.
The data may go through a series of multiple data cleansing procedures, 
such as value validition, data reformatting, duplicate elimination, and 
statistical analysis.
Since the inference data do not have labels, 
cleaned data are often directly be used for inference preprocessing.

.. _label_data:

Label Data
==========

In this activity, the data are labeled to support the supervised ML. 
(For unsupervised ML, this step may be skipped.)
The labeling process often involves manual labeling but can also be automated 
in some use cases. 
This aims to map each data point to the expected inference outputs.
An output can be a set of labels (for classification) or values (for regression).
A data scientist can use the labeled data set to experiment different ML models 
and tune the hyperparameters during ML design. 
After the ML model is designed and programmed, the labeld data set is used 
to train the model in the :doc:`training` work stream.

.. _preprocess_inference_inputs:

Preprocess Inference Inputs
===========================

In this activity, the cleaned and / or labeled data are transformed to 
the input format required by the inference application to process
in the :doc:`inference` work stream,
for example,
in form of API requests, a message stream, or a data file. 
How the inference input data should be constructed and submitted 
depends on the specific input requirements of the inference application.

.. _preprocess_training_sets:

Preprocess Training Data
========================

In this activity, the training data sets are produced for 
modeling :doc:`modeling` work stream
or training in the :doc:`training` work stream. 
The file format can be specific to the ML library used. 
The training data can be split into two sets: training set and 
testing set. The training set is used to train the model while
the testing set is used to validate the model for its accuracy.

.. _validate_inference_outputs:

Validate Inference Outputs
==========================

The outputs from the inference application 
in the :doc:`inference` work stream are fed back for validation
against the expected results. The outputs, 
especially those which are insufficiently accurate,
can be relabeled (manually) can be merged into the 
new training and testing sets
for retraining in the :doc:`training` work stream 
so as to continously improve the model.

