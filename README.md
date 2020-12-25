# Gender-Detection-using-CNN
  1. METHODOLOGY\
• An RGB image of a person is captured by IR Camera Module\
• The image is first scaled to 3 x 256 x 256 and then cropped to 3 x 227 x 227\
• Extraction of facial features from the image captured and analysis of face database\
• Training and testing of particular face dataset\
• Process of Convolutional Neural Network (CNN)\
• Classifcation of dataset which shows the result either male or female

  2. Hardware modules\
• Raspberry Pi 3\
• RPi Camera

  3. CONVOLUTIONAL NEURAL NETWORK\
i. 96 filters of size 3 x 7 x 7 pixels are applied to the input image in the
convolutional layer - 1 with 4 strides and zero padding, resulting output of size
96 x 96 x 56, which is followed by reduction of the size to 96 x 28 x 28, and a
Local Response Normalization (LRN).\
ii. The output of first is applied to convolutional layer - 2 with 256 filters of size 96
x 5 x 5 convolved with 1 stride and 2 padding, resulting output of size of 256 x
28 x 28. Which is further followed by ReLU, max-pool and LRN, reducing the
output size to 256 x 14 x 14.\
iii. This second output is applied to convolutional layer - 3 with again 256 filters of
size 256 x 3 x 3 are convolved with 1 stride and 1 padding, resulting in an output
of 256 x 7 x 7 size.\
 The fully connected layers are described as:\
• The first fully connected layers which receives the output of third convolutional
layer, has 512 neurons followed by a ReLU and dropout layer.\
• The second fully connected layer of 512 neurons fully connected to the 1 x 512
output of first fully connected layer followed by a ReLU and dropout layer.\
• The final fully connected layer with 2 or 8 neurons fully connected to the 1 x 512
output of second fully connected layer which maps to final classes of gender
detection.

   4. TRAINING AND TESTING OF DATASET\
The dataset used for testing and training for this implementation is Adience dataset which is
recently introduced by Open University of Israel (OUI) has approximately 26K face images
with 2,284 unique subjects. Various challenging levels like occlusion, lighting, and blur are
subjected with all these images. Here I have used mostly front face images near about 20K
images. This dataset is also used for gender as well as age prediction system . These all images
are of 768 x 768-pixel size which are being resized to 256 x 256.\
In order to produce the gender prediction for different – faces, two methods of using network
are introduced as follows:\
i. Center Crop: Images are cropped to 227 x 227 around the face center which are used to feed
the network\
ii. Over-sampling: five 227 x 227-pixel crop regions, four from the corners of the 256 x 256-
pixel face image with additional center crop of the face are extracted. From all these variations
the average prediction value is considered as a final prediction.

There is a noticeable impact on the quality of the result for the small misalignments in the
Adience face images caused by challenges like occlusions, motion blur etc. therefore to
compensate for this small misalignment, the oversampling is used to improve the alignment
quality.
