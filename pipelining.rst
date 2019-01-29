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

This activity labels the data points for supervised ML, if necessary. 
The labeling process often involves manual labeling but can be automated 
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

This activity preprocesses the cleaned or labeled data into an format
specific to the ML library used for modeling or training. For inference,
the data may need to be structured as specified by the inference application, 
for example, as an API request stream, or simply a data file. 
This can be automated using a preprocessor program or service.

.. _produce_data:

Produce Data
============

This activity feeds the preprocessed data to a ML library, program, or service
for modeling, training or inference.

.. _produce_modeling_data:

Produce Modeling Data
---------------------

This activity produces the data for feeding into the ML modeling software to facilitate
data exploration in the ML design time.

.. _produce_training_data:

Produce Training Data
---------------------

This activity produces a updated training data set for the recurrent ML training.

.. _produce_inference_data:

Produce Inference Data
----------------------

This activity produces the API request stream, or data file for the
inference application to process. How the inference data should be constructed
and submitted depends on the specific requirements of the inference application.

.. _validate_inference_results:

Validate Inference Results
==========================

The results produced by the inference application are fed back for validation
against the expected outputs. The results which are not sufficiently accurate
should be relabeled (possibly manually) and merged into the training data sets
for retraining so as to continously improve the ML model.

