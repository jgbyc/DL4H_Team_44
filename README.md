# CS598 DL4H Final Project

This is a repository for duplicating the paper "An attention based deep learning model of clinical events in the intensive care unit"
Original paper was written by Deepak A. KajiID1, John R. ZechID1, Jun S. Kim1, Samuel K. Cho1,2, Neha S. Dangayach2,3,Anthony B. Costa2, Eric K. Oermann2

### Getting Started

Following instructions will help to reproduce the result of orginal paper. All py files are adapted from https://github.com/deepak-kaji/mimic-lstm and updated to be able to run with Keras version 2.13.1, Tensorflow version 2.13.0

To begin, clone this repository. Within the repository, create a folder called, "mimic_database" where the MIMIC-III will live. Then, request access from https://mimic.physionet.org/gettingstarted/access/, complete the required training course, and request the access to MIMIC-III. Download all MIMIC-III CSVs to "./mimic_database".

process_mimic.py contains classes for transforming the MIMIC-III tables into a pandas dataframe with the required feature columns. Specifically, the MimicParser class will provide all required methods for this operation. Moreover, the exact methods required to build the dataframe are listed at the bottom of the script. In order for this script to function, a number of dependencies are required and listed below. The "./mimic_database" folder will require a './mimic_database/mapped_elements" folder inside of it for the production of MIMIC-III dataframe intermediates. The MimicParser sequentially moves through tables of the MIMIC-III adding pieces of what is required. Not all MimicParser methods are required for operation.

rnn_mimic.py contains classes for transforming the pandas dataframe into a 3rd order tensor (batch_size, time_steps, features). It will require pad_sequences as an included dependency. the pickle_objects method is reduced from the original one which is intended for training sets for vancomycin only. The train models will generate the models required for all figures. 

Models and figures are generated in the .ipynb notebook.

### Prerequisites
The pad_sequences.py file is required for rnn_mimic.py functionality. Additionally, the attention function adapted from Philippe Remy's Github has been cloned as attention_function.py and is required for the build_model function in rnn_mimic.py which assembles the LSTM-RNN with attention. All LSTM-RNNs were constructed in Tensorflow using the Keras API. Sklearn was used for validation metrics such as the AUROC. Numpy and Pandas libraries were required for table and matrix manipulation. 

get_activation function under attention_function.py is outdated so Keract.py is used in the .ipynb to handle generating of attention heatmap

### Authors
Kun Ren and Yichen Bi was the contributor for this repository. 


