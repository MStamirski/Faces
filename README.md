# Faces

Goal of this project was to create a model, which would recognize some features of faces on photos. These features are:
* sex of a person
* hair - long or short
* glasses
* hat
* beard

This was a multilabel classification problem in the field of computer vision.

#### Notebook "Photos preparation"
First task was to collect a set of appropriate photos. I found such pictures on iStock. I downloaded 10 of them, each one with different numbers of faces. They were all on square background, arranged in rectangles. I resized these pictures so that all faces got shape 64x64 pixels, converted to grayscale, cut faces, removed background and saved into separate files.

#### Notebook "Dataset_prep"
Set of saved faces was then processed in order to obtain a dataset, suitable for training neural network. First of all faces were labelled. During this process some of them were deleted, due to their low quallity, especially resulting from removing a background. It also turned out, that some of faces were repeated on different pictures. Therefore I decided to alter faces during loading, starting from picture number 5. Alterations were: flipping, rotating of 22 deg. left and right, narrowing and widening faces (keeping picture size unchanged). 

At this stage there was 1325 faces. Then I augmented this set by applying blur and zoom (with picture size unchanged). Finally I got dataset with 5300 different faces. In this notebook I included functions loading labels, processing faces and returning data with labels. These functions are imported in next notebooks.

#### Notebook "Dataset - presentation"
This notebook contains overview of labels before and after augmentation of dataset. It also shows some random faces with labels and their alteration during augmentation. While sex labels were quite balanced, the rest were not. The least balanced was label 'hat'.

#### Notebook "Functions"
Next step of data preparation was to normalize numbers of grayscale color (from 0 to 1 instead of 0-255) and replace labels coded in character with digits 0 or 1. Another functions were related to displaying results of model training and testing. 

Keeping in mind the fact of unbalanced labels, instead of downsampling or upsampling data, I used a method of threshold tuning. Assignment a prediction of model (which is a fraction number) to class 0 or 1 of each label depends on assumed threshold, which is by default 0.5. In case of unbalanced data the best threshold may be different. For given test and predicted targets I calculated F1 score (based on recall and precision) for different thresholds from range 0.5 - 0.95. The final threshold was chosen for the highest F1. On the basis of this threshold and results of model predictions, I created tuned target dataset with predicted labels.

Results of prediction made on separate test dataset could be presented as a list of several random samples, with face picture and comparison of ground truth values to predictions. Good predictions are printed in green, false in red.

Functions performing above tasks for only one label prediction are included in this notebook.

#### Notebook "Functions_all_labels"
Here we have some functions, changed comparing to described above, in order to deal with multilabel prediction.

#### Notebooks "Model - ..."
There are several notebooks with analogous structure, where a Sequential model (keras library) is built, trained and tested - for each one of all labels. The structure of models is a result of some trials. All of them contain 3 convolutional layers. They were trained in 20 epochs, with "adam" optimizer and "binary crossentropy" loss function. History of training is shown on diagrams, as well as results of predictions.

#### Notebook "Model - all"
