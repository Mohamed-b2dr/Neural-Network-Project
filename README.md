# Neural-Network-Project
  ## Skin cancer using Deep Learning

# Define the problem

Skin cancer is a dangerous and widespread disease Each year there are approximately 5.4 million new cases of skin cancer are recorded in the USA alone.
The global statistics are equally alarming. 
Recent reports show that from 2008 to 2018, there has been a 53% increase in new melanoma cases diagnosed annually. 
The mortality rate of this disease is expected to rise in the next decade.
The survival rate is less than 14% if diagnosed in later stages.

# Motivation
If skin cancer is detected at early stages then the survival rate is nearly 97% [3]. This demands the early detection of skin cancer. This paper addresses the issue of early diagnosis, with improved accuracy.

It is found that a skilled dermatologist usually follows a series of steps, starting with the naked-eye observation of suspected lesions, then dermoscopy (magnifying lesions microscopically), and followed by a biopsy. This would consume time and the patient may advance to later stages. Moreover, accurate diagnosis is subjective, depending on the skill of the clinician. It is found that the best dermatologist has an accuracy of less than 80% incorrectly diagnosing skin cancer. Adding to these difficulties, there are not many skilled dermatologists available globally in public healthcare.

To diagnose skin cancer speedily at the earliest stage and solve some of the aforementioned problems, there have been extensive research solutions by developing computer image analysis algorithms. The majority of these algorithmic solutions were parametric, meaning that they required data to be normally distributed. As the nature of data cannot be controlled, these methods would be insufficient to accurately diagnose the disease. However, non-parametric solutions do not rely on the constraint that the data is in normal distribution form.

Our Model augmented assistance to the dermatologist is provided using deep learning. The essence of the approach is that a computer is trained 
to determine the problem by analyzing the skin cancer images.

# Dataset
The dataset was generated by the International Skin Imaging Collaboration (ISIC) and images are from the following sources: Hospital Clínic de Barcelona, Medical University of Vienna, Memorial Sloan Kettering Cancer Center, Melanoma Institute Australia, University of Queensland, and the University of Athens Medical School.

# Input & Output 
Developing a DeepLearningmodel to classify skin cancer images
into 9 different categories with high enough accuracy to be
reliable.

Those categories are

* actinic keratosis 
* basalcellcarcinoma 
* dermatofibroma 
* melanoma 
* nevus 
* Pigmentedbenignkeratosis
* seborrheic keratosis 
* squamouscellcarcinoma 
* vascular lesion

# Related work: 
What has been done? 
The paper we used relied on VGG-16 which resulted in an accuracy of 69.57 % while the theVGG-19 had a better accuracy of 71.19% 

The paper also did some preprocessing on the images such as
Augmentationsetting   Range
rotation range               90 
shear range                  0.1
zoom range                  0.14 
horizontal flip                True

What are the problems?
* They are more attention to models than distribution data.

# Working about data:
Datasets  4600 images, which is very small for 9 class, in addition, data is imbalanced and have very bad distribution.

So, We working to solve this.

* Firstly, we split data into two partitions final set & train set, then worked in data training to increase images and slove distribution.
* We making Augmentation using 
Python package is known as Augmentor (https://augmentor.readthedocs.io/en/master/) to add more samples across all classes so that none of the classes have very few samples
    - Instantiate a Pipeline object pointing to a directory containing your initial image data set.
    - Define several operations to perform on this data set using your Pipeline object.
    - Execute these operations by calling the Pipeline’s sample() method.
* Finally, we split data training to train & validation, we worried that this approach makes overfitting, so, we split from data partition to data set.


# Algorithm:
 * We Used  Xception.

* Our data is not very large, so transfer learning is a very good option, we do not make unfreeze layer also this problem dissimilar problem, but we used it as an initial weight instead of 
We use Random initial weight, this option gives us a good result.

* Also, we added some layers
  - GlobalAveragePooling2D
  - Dropout
  - BatchNormalization
  - Dense
* Using optimizers Adam with learning_rate= 3e-4
* Using callbacks with 
  - early stopping 
  - ReduceLROnPlateau to reduce the learning rate the confusion metric has stopped improving. 
 

* Accuracy with 
  - Validation 94
  - final test 91

# Evaluation:
* We used the classification report to show the precision, recall, F1 Score, weighted average, and micro average.
* We used confusion_matrix in the final test to know the conflict with classes
###            Validation Result
![Validation Result](https://github.com/Mohamed-b2dr/Neural-Network-Project/blob/master/Screenshot%202022-05-23%20145753.png)

###            Final Result
![Final Result](https://github.com/Mohamed-b2dr/Neural-Network-Project/blob/master/Screenshot%202022-05-23%20145818.png)

 ###          Confusion Matrix in the final test
![Confusion Matrix in the final test](https://github.com/Mohamed-b2dr/Neural-Network-Project/blob/master/download.png)
# Analysis
*  Our results are very good with another solution, but not very good for the medical field.
* We Noticed, Model, did not good t0 difference between:
  - Actinic & Nevus
  - seborrheic keratosis & melanoma
## In our future, the plan is to work around data to solve this problem
* Our solution we working on using some preprocessing in data to solve this conflict.

* Another solution, make our system consist of two layers and merge Actinic & Nevus in one category and seborrheic keratosis & melanoma in one category, and layer two have two models of binary classification if the result is one of the merged categories, the disadvantage will resources usages

