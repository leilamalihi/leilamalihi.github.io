---
title: "Klix"
excerpt: "Preparing LCW: a dataset for children 1<br/><img src='/images/face.png'>"
collection: portfolio
---
- In [klix](https://www.ikw.uni-osnabrueck.de/research_groups/computer_vision/research/klix.html) project, we proposed a novel dataset ”Labeled Children in the Wild” (LCW) for facial recognition tasks, that features are more challenging (high variance) for modern face recognition solutions and freely available.
- We use a model that was pre-trained on [VGGFace]( https://www.robots.ox.ac.uk/~vgg/software/vgg_face/) and fine-tune its weights by training on our dataset [(Refer to my paper)](/files/face_recognition_of_children__India_2_.pdf)

Measuring the quality of face recognizers adequately and quantifying improvements is crucial for further developing face recognizers. A popular dataset for evaluation is the LFW (Labeled Faces in the Wild) dataset. While this dataset is widely accepted in the community as a benchmark, it could be argued that the dataset is also saturated with recent models achieving over 99% accuracy. This can be considered problematic for improvements up to this point have to be very small increments, making the effects of changes in the recognizers hard to quantify. We introduced a novel dataset ”Labeled Children in the Wild” (LCW) with a structure similar to LFW to serve as a drop-in-replacement for LFW. The data is selected to be more difficult, featuring additional challenges that can occur in recognition scenarios. These involve such challenges as strong age differences, ranging from early childhood to very high ages, strong use of costumes and makeup, as well as a strong variety of source media. The dataset features photographs as well as frames from films and movies. The images were recorded under heterogeneous conditions between 1870 and 2019, featuring a wide range of scenarios, camera technology and image quality.

Baseline accuracies using Keras-vggface developed for testing the face identification across the age progression on a subset of the HV-LFW dataset. We used Keras (version 2.4.3) and the GPU version of TensorFlow (2.2.0) to perform transfer learning on the LCW dataset. This model was trained on a large dataset containing 2.6M images of 2,622 identities. Identification results on images of HV-LFW age progression subset can be seen in following:

![Real Or Synthetic](/images/facedet.png)
