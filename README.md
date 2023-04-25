# Faces

Goal of this project was to create a model, which would recognize some features of faces on photos. These features are:
* sex of a person
* hair - long or short
* glasses
* hat
* beard

#### Notebook "Photos preparation"
First task was to collect a set of appropriate photos. I've found such pictures on iStock. I downloaded 10 of them, each one with different numbers of faces. They were all on square background, arranged in rectangles. I resized these pictures so that all faces got shape 64x64 pixels, converted to grayscale, cut faces, removed background and saved into separate files.
#### Notebook "Dataset_prep"
Set of saved faces was then processed in order to obtain a dataset, suitable for training of neural network. First of all faces were labelled. During this process some of them were deleted, due to their low quallity, especially resulting from removing a background. It also turned out, that some of faces were repeated on different pictures. Therefore I decided to alter faces during loading, starting from picture number 5. Alterations were: flipping, rotating of 22 deg. left and right, narrowing and widening faces (keeping picture size unchanged). 

At this stage there was 1325 faces. Then I augmented this set by applying blur and zoom (with picture size unchanged). Finally I got dataset with 5300 different faces. In this notebook I included functions loading labels, processing faces and returning data with labels. These functions are imported in next notebooks.
#### Notebook "Dataset - presentation"
This notebook contains overview of labels before and after augmentation of dataset. It also shows some random faces with labels and their alteration during augmentation. While sex labels were quite balanced, the rest were not. The least balanced was label 'hat'.
### 
