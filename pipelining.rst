**********
Pipelining
**********

Introduction
============
The first swimlane in :numref:`yamflowchart` illustrates the Pipelining
workstream. 
The Pipelining work stream prepares the data sets and data streams for 
ML modeling, training, and inference. 
It consists of the following activities:

- `Acquire Data`_ aggregates the necessary data from the backend data sources 
  (e.g., databases) into raw data sets for ML modeling, training, and inference. 
- `Clean Data`_ cleans the aggregated data if necessary so that the data 
  quality is sufficient for labeling or preprocessing.
- `Label Data`_ annotates the data points with labels for ML training. 
  Manual curation may be mecessary.
- `Preprocess Inference Inputs`_ transforms the cleaned data into the specific input 
  format reqired by the inference application.
- `Preprocess Training Sets`_ transforms the labeled data into the training 
  data files suitable for experimentation or training.
- `Validate Inference Outputs`_ validates the inference results, which may
  involve manual curation. Inaccurate results may be relabeled for future 
  training.

.. _acquire_data:

Acquire Data
============

This activity acquires the necessary raw data sets for ML modeling, training, 
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

This activity improves the quality of the data sets up to the standard 
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

This activity labels the data points for supervised ML, if necessary. 
The labeling process often involves manual labeling but can also be automated 
in some use cases. This aims to map each data point to the expected inference 
results, which can be a set of labels (for classification) or values (for regression).
A data scientist can use the labeled data set to experiment various ML models 
and tune the hyperparameters during ML design. 
After the ML model is designed and programmed, the labeld data set will be used 
to train the model for serve inference. 
For unsupervised ML, this step may be skipped.

.. _preprocess_inference_inputs:

Preprocess Inference Inputs
===========================

This activity produces the API requests, the message stream, or the data file 
for the inference application to process. How the inference data should be constructed
and submitted depends on the specific input requirements of the inference application.

.. _preprocess_training_sets:

Preprocess Training Sets
========================

This activity produces the training data file for modeling or training. 
The file format can be specific to the ML library used.

.. _validate_inference_outputs:

Validate Inference Outputs
==========================

The outputs from the inference application are fed back for validation
against the expected results. The outputs which are  insufficiently accurate
can be relabeled (manually) and merged into a new training data set
for retraining so as to continously improve the model.

