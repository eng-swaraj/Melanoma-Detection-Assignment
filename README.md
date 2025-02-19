# CNN Architecture: Melanoma Detection - Assignment
Melanoma is the deadliest form of skin cancer among over 200 types. Its diagnosis generally starts with clinical screening, followed by dermoscopy and histopathology. Early detection is crucial for effective treatment. Dermatologists use high-speed cameras for visual inspection, achieving 65-80% accuracy in diagnosis. With additional expert analysis, accuracy increases to 75-84%. The project aims to develop an automated system using image processing to classify skin cancer from lesion images.

## Problem statement

To build a CNN based model which can accurately detect melanoma. Melanoma is a type of cancer that can be deadly if not detected early. It accounts for 75% of skin cancer deaths. A solution that can evaluate images and alert dermatologists about the presence of melanoma has the potential to reduce a lot of manual effort needed in diagnosis.

## Class Distribution

Class with the fewest samples: Seborrheic keratosis
Class dominating the dataset: Pigmented benign keratosis
To balance this, we employ proportional augmentation using zoom, since the images are centered.


## Model Designing Approach

Here's a step-by-step breakdown of the final CNN architecture:
Data Augmentation: The augmentation_data variable encompasses techniques like rotation, scaling, and flipping to expand the diversity of the training set, enhancing the model's ability to generalize.

Normalization: A Rescaling(1./255) layer normalizes image pixel values to a 0-1 range, aiding in quicker and more stable model training.

Convolutional Layers: We use three Conv2D layers, each followed by a ReLU activation for non-linearity. The layers use 16, 32, and 64 filters, respectively, with 'same' padding to maintain output size.

Pooling Layers: Each Conv2D layer is followed by a MaxPooling2D layer to reduce spatial dimensions, decrease computation, and help prevent overfitting.

Dropout Layer: A Dropout layer with a rate of 0.2 is introduced post-pooling to combat overfitting by randomly deactivating neurons during training.

Flatten Layer: The Flatten layer converts the 2D feature maps into a 1D vector for dense layers.

Fully Connected Layers: Two Dense layers follow, with the first having 128 neurons and using ReLU activation, preparing the data for final classification.

Output Layer: The final Dense layer's neuron count matches the number of classes (target_labels). No activation is specified here as it's handled by the loss function.

Model Compilation: The model uses the Adam optimizer, Sparse Categorical Crossentropy loss (suitable for multi-class classification), and tracks accuracy.

Training: The model is trained for 30 epochs using the fit method, allowing it to learn from the data over multiple iterations.
 

## Model Summary

Epoch 1/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m358s[0m 2s/step - accuracy: 0.3506 - loss: 2.2556 - val_accuracy: 0.1111 - val_loss: 4.2527
Epoch 2/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m335s[0m 1s/step - accuracy: 0.5580 - loss: 1.4133 - val_accuracy: 0.3467 - val_loss: 2.1754
Epoch 3/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m335s[0m 1s/step - accuracy: 0.6396 - loss: 1.1179 - val_accuracy: 0.5789 - val_loss: 1.2512
Epoch 4/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m338s[0m 2s/step - accuracy: 0.7207 - loss: 0.8641 - val_accuracy: 0.6694 - val_loss: 0.9570
Epoch 5/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m344s[0m 2s/step - accuracy: 0.7498 - loss: 0.7553 - val_accuracy: 0.6394 - val_loss: 1.0832
Epoch 6/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m336s[0m 1s/step - accuracy: 0.7714 - loss: 0.6875 - val_accuracy: 0.6833 - val_loss: 1.0292
Epoch 7/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m334s[0m 1s/step - accuracy: 0.8345 - loss: 0.5071 - val_accuracy: 0.7450 - val_loss: 0.7971
Epoch 8/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m336s[0m 1s/step - accuracy: 0.8421 - loss: 0.4622 - val_accuracy: 0.7550 - val_loss: 0.7746
Epoch 9/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m337s[0m 1s/step - accuracy: 0.8704 - loss: 0.3769 - val_accuracy: 0.7656 - val_loss: 0.8327
Epoch 10/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m338s[0m 1s/step - accuracy: 0.8825 - loss: 0.3373 - val_accuracy: 0.5661 - val_loss: 1.8894
Epoch 11/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m338s[0m 2s/step - accuracy: 0.9059 - loss: 0.2747 - val_accuracy: 0.7528 - val_loss: 0.8383
Epoch 12/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m342s[0m 2s/step - accuracy: 0.9080 - loss: 0.2730 - val_accuracy: 0.7794 - val_loss: 0.7527
Epoch 13/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m378s[0m 2s/step - accuracy: 0.9081 - loss: 0.2621 - val_accuracy: 0.7939 - val_loss: 0.5718
Epoch 14/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m317s[0m 1s/step - accuracy: 0.9063 - loss: 0.2619 - val_accuracy: 0.7233 - val_loss: 1.0296
Epoch 15/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m297s[0m 1s/step - accuracy: 0.9188 - loss: 0.2408 - val_accuracy: 0.7689 - val_loss: 0.8397
Epoch 16/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m299s[0m 1s/step - accuracy: 0.9251 - loss: 0.2168 - val_accuracy: 0.7572 - val_loss: 0.8744
Epoch 17/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m352s[0m 2s/step - accuracy: 0.9308 - loss: 0.2045 - val_accuracy: 0.7350 - val_loss: 0.8774
Epoch 18/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m336s[0m 1s/step - accuracy: 0.9229 - loss: 0.2114 - val_accuracy: 0.7922 - val_loss: 0.6940
Epoch 19/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m338s[0m 2s/step - accuracy: 0.9249 - loss: 0.2081 - val_accuracy: 0.7522 - val_loss: 0.9622
Epoch 20/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m337s[0m 1s/step - accuracy: 0.9338 - loss: 0.1834 - val_accuracy: 0.7800 - val_loss: 0.6978
Epoch 21/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m319s[0m 1s/step - accuracy: 0.9403 - loss: 0.1728 - val_accuracy: 0.7761 - val_loss: 0.7410
Epoch 22/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m319s[0m 1s/step - accuracy: 0.9291 - loss: 0.1838 - val_accuracy: 0.7428 - val_loss: 0.8935
Epoch 23/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m312s[0m 1s/step - accuracy: 0.9341 - loss: 0.1641 - val_accuracy: 0.8044 - val_loss: 0.6558
Epoch 24/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m307s[0m 1s/step - accuracy: 0.9437 - loss: 0.1524 - val_accuracy: 0.7600 - val_loss: 0.8107
Epoch 25/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m315s[0m 1s/step - accuracy: 0.9542 - loss: 0.1352 - val_accuracy: 0.7861 - val_loss: 0.9018
Epoch 26/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m333s[0m 1s/step - accuracy: 0.9410 - loss: 0.1587 - val_accuracy: 0.7067 - val_loss: 1.1844
Epoch 27/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m300s[0m 1s/step - accuracy: 0.9406 - loss: 0.1624 - val_accuracy: 0.7500 - val_loss: 0.8891
Epoch 28/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m307s[0m 1s/step - accuracy: 0.9264 - loss: 0.2013 - val_accuracy: 0.6528 - val_loss: 1.5449
Epoch 29/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m335s[0m 1s/step - accuracy: 0.9443 - loss: 0.1458 - val_accuracy: 0.7867 - val_loss: 0.7479
Epoch 30/30
[1m225/225[0m [32m━━━━━━━━━━━━━━━━━━━━[0m[37m[0m [1m310s[0m 1s/step - accuracy: 0.9380 - loss: 0.1652 - val_accuracy: 0.8011 - val_loss: 0.7273


## Contact
Created by Swaraj ML-C67 