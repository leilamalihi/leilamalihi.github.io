---
title: "ZIEL"
excerpt: "Wound classification and Generating <br/><img src='/images/Sc.png'>"
collection: portfolio
---
Can AI detect the Wound part?

Chronic wounds are ulcerations of the skin that fail to heal because of an underlying condition such as diabetes mellitus or venous insufficiency. The timely identification of this condition is crucial for healing. However, this identification requires expert knowledge unavailable in some care situations. Here, artificial intelligence technology may support clinicians. In this study, we explore the performance of a deep convolutional neural network to classify diabetic foot and venous leg ulcers using wound images. We trained a Xception model on 863 cropped wound images. Using a hold-out test set with 80 images, the model yielded an F1-score of 0.85 on the cropped and 0.70 on the full images. This study shows promising results. However, the model must be extended in terms of wound images and wound types for application in clinical practice.Grad-CAM is an algorithm visualizing the salient features in the last convolutional layer that mainly drives the final classification. We used that to hilight the wound part.

 ![Real Or Synthetic](/images/grad.png)
 *Detecting the wound part by Xception model 

 - Using deep neural Xception model, the wound part detected.
 - The wound part hilighted by Grad-cam.[(Refer to my paper)](https://pubmed.ncbi.nlm.nih.gov/35773863/)

  ![Real Or Synthetic](/images/compare.png)
    *comparing the results, the left one is croped and the right one is uncropped images
    
 ---

# Generate Syntethic wound Images

![Real Or Synthetic](/images/w6.png)

- the left one is real and the right one is synthetic. We generated such thoes Images.
- In [ZIEL project](https://www.hs-osnabrueck.de/ziel/aktuelles/#c12675179), we generated 100,000 synthetic wound Images using [StyleGan3](https://nvlabs.github.io/stylegan3/). [(Refer to my paper)](https://pubmed.ncbi.nlm.nih.gov/37203538/).

