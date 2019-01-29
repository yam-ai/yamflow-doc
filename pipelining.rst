**********
Pipelining
**********

Introduction
============

The Pipelining work stream prepares the data sets and data streams for 
ML modeling, training, and inference. 
It consists of the following activities:

- `Acquire Data`_ aggregates the necessary data from the backend data sources 
  (e.g., databases) into raw data sets for ML modeling, training, and inference. 
- `Clean Data`_ cleans the aggregated data if necessary so that the data 
  quality is sufficient for labeling or preprocessing.
- `Label Data`_ annotates the data points with labels for ML training. 
  Manual curation may be mecessary.
- `Preprocess Data`_ preprocesses the data into the formats suitable for ML
  modeling, training, and inference.
- `Produce Data`_ produces the following data.

  - `Produce Modeling Data`_ produces the data sets necessary for 
    desiging the ML model.
  - `Produce Training Data`_ produces the training and validation data sets.
  - `Produce Inference Data`_ produces the data sets or streams for inference.

- `Validate Inference Results`_ validates the inference results, which may
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

This activity labels the data points, if necessary, for supervised ML. 
The labeling process  often involves manual labeling but can be automated 
in some use cases. This aims to map each data point to the expected outputs,
which can be a set of labels (for classification) or values (for regression).
A data scientist can use the labled data set to experiment various ML models 
and turn the hyperparameters during ML design. 
After the ML model is designed and programmed, the labeld data set will be used 
to train the model for serve inference. 
For unsupervised ML, this step may be skipped.

.. _preprocess_data:

Preprocess Data
===============

.. _produce_data:

Produce Data
============

.. _produce_modeling_data:

Produce Modeling Data
---------------------

.. _produce_training_data:

Produce Training Data
---------------------

.. _produce_inference_data:

Produce Inference Data
----------------------

.. _validate_inference_results:

Validate Inference Results
==========================

