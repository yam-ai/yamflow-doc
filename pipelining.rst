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

  - `Produce Experimental Data`_ produces the data sets necessary for 
    desiging the ML model.
  - `Produce Training Data`_ produces the training and validation data sets.
  - `Produce Inference Data`_ produces the data sets or streams for inference.

- `Validate Inference Results`_ validates the inference results, which may
  involve manual curation. Inaccurate results may be relabeled for future 
  training.

.. _acquire_data:

Acquire Data
============

.. _clean_data:

Clean Data
==========

.. _label_data:

Label Data
==========

.. _preprocess_data:

Preprocess Data
===============

.. _produce_data:

Produce Data
============

.. _produce_experimental_data:

Produce Experimental Data
-------------------------

.. _produce_training_data:

Produce Training Data
---------------------

.. _produce_inference_data:

Produce Inference Data
----------------------

.. _validate_inference_results:

Validate Inference Results
==========================

