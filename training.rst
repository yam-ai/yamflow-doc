********
Training
********

Introduction
============
The third swimlane in :numref:`yamflowchart` illustrates the Training work stream.
In this work stream, the ML model coded in the :doc:`modeling` work stream 
is trained and validated; the validated trained model is registered for 
deployment in the :doc:`inference` work stream. 
The activities in this work stream can be done mannually,
or automated whereever possible especially for recurrent training. 

+--------------------------------+---------------------------------------------------------+-------------------+--------------------+
| Activity                       | Description                                             | Inputs            | Outputs            |
+================================+=========================================================+===================+====================+
| `Train Model`_                 | The pre-trained ML model coded in the :doc:`modeling`   | Pre-trainined     | Trained model      | 
|                                | work stream is trainined with a updated training set    | model &           |                    |
|                                | using the selected hyperparameters.                     | hyperparameters & |                    |
|                                |                                                         | training          |                    |
|                                |                                                         | set               |                    |
+--------------------------------+---------------------------------------------------------+-------------------+--------------------+
| `Validate Model`_              | The new trainied ML model is validated with a testing   | Trained model &   | Validated model    |
|                                | set on the inference accuracy. Only the model with an   | testing set       |                    |
|                                | expected accuracy is used for deployment.               |                   |                    |
+--------------------------------+---------------------------------------------------------+-------------------+--------------------+
| `Register Model`_              | The validated model with an expected accuracy is        | Validated         | Trained model      |
|                                | registered to the registry for deployment to the        | model             | published to       |
|                                | :doc:`inference` work stream.                           |                   | registry           |
+--------------------------------+---------------------------------------------------------+-------------------+--------------------+

.. _train_model:

Train Model
===========

The coded ML model and the selected hyperparameters from the :doc:`modeling` work stream 
are passed to this activity. 
The pre-trainined ML model is recurrently trained when a updated training set is generated.
This activity can be done mannually. 
If the trained model needs to be updated regularly, the training process should be        
programmatically automated.
Note that the training set should be representative of the current data pattern for inference.

.. _validate_model:

Validate Model
==============

The newly trained model is validated against performing inference on a testing set. 
A validation rule can be set to define the criteria on the acceptance of an updated
trained model. 
For example, the `precision and recall <https://en.wikipedia.org/wiki/Precision_and_recall>`_ 
of the updated trained model must be above predefined thresholds. 
Note that the testing set should be representative of the current data pattern for inference.

.. _register_model:

Register Model
==============

The trained model accepted after validation can be registered to a registry for deployment
to the :doc:`inference` work stream.

