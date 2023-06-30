---
title: "ZIEL"
excerpt: "Wound Identification and Generating <br/><img src='/images/ziel.png'>"
collection: portfolio
---
[(ZIEL)](https://www.hs-osnabrueck.de/ziel/aktuelles/#c12675179) is funded by the Federal Ministry of Education and Research (BMBF). The network consists of five scientific and two technical partners. The project is scientifically supervised by the research group "Informatics in Health Care" at the Osnabrück University of Applied Sciences, the "Computer Vision" working group at the Institute for Cognitive Sciences and the Department for "Public Health" at the Institute for Health Research and Education at the University of Osnabrück, the Dermatological Clinic of the University Hospital Erlangen and the Department of Dermatology at the University Hospital Essen. The technical implementation is carried out by apenio GmbH and Symbic GmbH. The consortium leader is the Osnabrück University of Applied Sciences.

# Can AI detect the Wound part?

Chronic wounds are ulcerations of the skin that fail to heal because of an underlying condition such as diabetes mellitus or venous insufficiency. The timely identification of this condition is crucial for healing. However, this identification requires expert knowledge unavailable in some care situations. Here, artificial intelligence technology may support clinicians. In this study, we explore the performance of a deep convolutional neural network to classify diabetic foot and venous leg ulcers using wound images. We trained a Xception model on 863 cropped wound images. Using a hold-out test set with 80 images, the model yielded an F1-score of 0.85 on the cropped and 0.70 on the full images. This study shows promising results. However, the model must be extended in terms of wound images and wound types for application in clinical practice.Grad-CAM is an algorithm visualizing the salient features in the last convolutional layer that mainly drives the final classification. We used that to hilight the wound part.

 ![Real Or Synthetic](/images/grad.png)
 $Detecting$  $the$  $wound$  $part$ $by$ $Xception$ $model$

 - Using deep neural Xception model, the wound part detected.
 - The wound part hilighted by Grad-cam.[(Refer to my paper)](https://pubmed.ncbi.nlm.nih.gov/35773863/)

  ![Real Or Synthetic](/images/compare.png)
  
  $Indentification$ $Wound$ $Images$ , $dfu$ $means$ $dayabetic$ $and$ $ucv$ $means$ $venous$
    
 ---

# Generate Syntethic wound Images
Machine Learning (ML) based AI systems require a large amount of labelled training data to achieve this level. In cases of a shortage of such large amounts, Generative Adversarial Networks (GAN) are a standard tool for synthesising artificial training images that can be used to augment the data set. We investigated the quality of synthetic wound images regarding two aspects: (i) improvement of wound-type classification by a Convolutional Neural Network (CNN) and (ii) how realistic such images look to clinical experts (n = 217). Concerning (i), results show a slight classification improvement. However, the connection between classification performance and the size of the artificial data set is still unclear. Regarding (ii), although the GAN could produce highly realistic images, the clinical experts took them for real in only 31% of the cases. It can be concluded that image quality may play a more significant role than data size in improving the CNN-based classification result. 
![Real Or Synthetic](/images/w6.png)

- the left one is real and the right one is synthetic. We generated such thoes Images.
- In [ZIEL project](https://www.hs-osnabrueck.de/ziel/aktuelles/#c12675179), we generated 100,000 synthetic wound Images using [StyleGan3](https://nvlabs.github.io/stylegan3/). [(Refer to my paper)](https://pubmed.ncbi.nlm.nih.gov/37203538/).

