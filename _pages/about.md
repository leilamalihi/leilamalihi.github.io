---
permalink: /
title: "About Me"
excerpt: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---


Since 2020, I am research associate in Osnabrück university. Here we had two nice projects about [Wound detection](https://www.hs-osnabrueck.de/ziel/aktuelles/#c12675179) and [Face recognition](https://www.ikw.uni-osnabrueck.de/research_groups/computer_vision/research/klix.html). From 2021-2023, I taught [Advance topic in deep learning](https://leilamalihi.github.io/teaching/2014-spring-teaching-1) and [Machine learning](https://leilamalihi.github.io/teaching/2014-spring-teaching-1) course in Osnabrück university.  From 2013-2020, I was lecturer  at the Payame Noor University and University of Applied Science and Technology, which I had different [courses](https://leilamalihi.github.io/teaching/) like: Electronic, Image processing, Signal and system,Linear control, Electronic Labs. My master was Electrical engineering and my interest fields of research are deep learning, knowledge distillation, transfer learning, Feature visualization,  Machin learning and medical image processing. 


# LCW: a dataset for children 
![Real Or Synthetic](/images/face.png)
*Some images of LCW dataset*

- You can not access to a  public child face dataset?
- Your dataset is noisy? 
- You need more identities
- Use the [(LCW)](https://drive.google.com/drive/folders/1eHmgUfvix0bE7zg9ezY8joOv39r_4o3- ) dataset
- In [klix](https://www.ikw.uni-osnabrueck.de/research_groups/computer_vision/research/klix.html) project, we proposed a novel dataset ”Labeled Children in the Wild” (LCW) for facial recognition tasks, that features are more challenging (high variance) for modern face recognition solutions and freely available.
- We use a model that was pre-trained on [VGGFace]( https://www.robots.ox.ac.uk/~vgg/software/vgg_face/) and fine-tune its weights by training on our dataset [(Refer to my paper)](/files/face_recognition_of_children__India_2_.pdf)
Measuring the quality of face recognizers adequately and quantifying improvements is crucial for further developing face recognizers. A popular dataset for evaluation is the LFW (Labeled Faces in the Wild) dataset. While this dataset is widely accepted in the community as a benchmark, it could be argued that the dataset is also saturated with recent models achieving over 99% accuracy. This can be considered problematic for improvements up to this point have to be very small increments, making the effects of changes in the recognizers hard to quantify. We introduced a novel dataset ”Labeled Children in the Wild” (LCW) with a structure similar to LFW to serve as a drop-in-replacement for LFW. The data is selected to be more difficult, featuring additional challenges that can occur in recognition scenarios. These involve such challenges as strong age differences, ranging from early childhood to very high ages, strong use of costumes and makeup, as well as a strong variety of source media. The dataset features photographs as well as frames from films and movies. The images were recorded under heterogeneous conditions between 1870 and 2019, featuring a wide range of scenarios, camera technology and image quality.

Baseline accuracies using Keras-vggface developed for testing the face identification across the age progression on a subset of the HV-LFW dataset. We used Keras (version 2.4.3) and the GPU version of TensorFlow (2.2.0) to perform transfer learning on the LCW dataset. This model was trained on a large dataset containing 2.6M images of 2,622 identities. Identification results on images of HV-LFW age progression subset can be seen in following:

![Real Or Synthetic](/images/facedet.png)

---

# Can AI detect the Wound part?

 ![Real Or Synthetic](/images/Sc.png)
         *Detecting the wound part by Xception model*

 - Using deep neural Xception model, the wound part detected.
 - The wound part marked by Grad-cam.[(Refer to my paper)](https://pubmed.ncbi.nlm.nih.gov/35773863/)
 
 ---

# Can you realize the real one?

![Real Or Synthetic](/images/w6.png)

- I guss you could't realize that. In this figure, the *left* one is *real* and the *right* one is *synthetic*. We generated such thoes Images.
- In [ZIEL project](https://www.hs-osnabrueck.de/ziel/aktuelles/#c12675179), we generated 100,000 synthetic wound Images using [StyleGan3](https://nvlabs.github.io/stylegan3/). [(Refer to my paper)](https://pubmed.ncbi.nlm.nih.gov/37203538/).

---
# Malaria parasite detection
![Real Or Synthetic](/images/ma4.png)
*Extracting red blood cell mask, left is the blood cell image, right is red blood cell mask*

- A method to detect malaria parasite in blood samples stained with giemsa.
- Most of malaria parasites exist in red blood cells.
- At the first step, the red blood cell mask is extracted.
- Color histogram, granulometry, gradient and flat texture features are extracted
- Different classifires and combination methods applied [(Refer to my paper)](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6780011)


