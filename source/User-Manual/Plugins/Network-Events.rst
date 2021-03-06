.. _networkevents:
.. role:: raw-html-m2r(raw)
   :format: html


################
Network Events
################

.. image:: ../../_static/images/plugins/networkevents/networkevents-01.png
  :alt: Annotated Merger editor

|

.. csv-table:: Checks for incoming messages and adds them to the signal processing stream as timestamped strings. These messages can be sent from another program on the same machine, or a different machine on the same network.
   :widths: 18, 80

   "*Plugin Type*", "Source"
   "*Platforms*", "Windows, Linux, macOS"
   "*Built in?*", "No"
   "*Key Developers*", "Shay Ohayon, Josh Siegle, Aarón Cuevas López, Christopher Stawarz, Arne Meyer"
   "*Source Code*", "https://github.com/open-ephys-plugins/NetworkEvents"

Plugin configuration
########################

Since the Network Events module sends events, and not continuous data, it needs to be used in conjunction with another source. The best way to do this is with a Merger, with both the Network Events module and the other source feeding into the same signal chain.

It uses the `ZeroMQ`_ library under the hood.


Remote control commands
################################################

The network events module provides features for controlling data acquisition and recording functions.

The following commands are available:

:code:`StartAcquisition` – Starts data aquisition

:code:`StopAcquisition` – Stops data aquisition

:code:`StartRecord [CreateNewDir=1] [RecDir=recording_directory_path] [PrependText=some_text] [AppendText=some_text]` – Starts recording of data

The last command includes ptional keyword arguments of the form :code:`kwarg=value`:

* :code:`CreateNewDir` – creates a new (sub)directory with the current date string

* :code:`RecDir` – sets the recording directory

* :code:`PrependText` – sets the text to be prepended to the date string

* :code:`AppendText` – sets the text to be appended to the date string

:code:`StopRecord` – Stops recording


Example Code
##################

Matlab
-------
In the GUI's `Matlab Resources`_ folder, you'll find a :code:`matlab_zeroMQ_wrapper_example.m`, which shows how to send messages. Assuming the zeroMQ mex file is in the same directory (which it should be by default), all you have to do is initialize the connection using 'StartConnectThread' and the appropriate url, then send a message using 'Send', the handle of your connection, and the string you want. 

Python
--------
An Python example can be found at in the `Python Resources`_ folder: :code:`record_control_example_client.py`


.. _ZeroMQ: https://zeromq.org/
.. _Matlab Resources: https://github.com/open-ephys/plugin-GUI/tree/master/Resources/Matlab
.. _Python Resources: https://github.com/open-ephys/plugin-GUI/tree/master/Resources/Python




