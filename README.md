# AI - Deepfake Detection
- This project aims at Deepfake Detection.  
- Therefore, two models are needed to generate fake images and distinguish fake images.  
- We generated fake images using **stable diffusion**, and created a detection model using **Lora and single center loss**.  

## Generator Strategy
- Generative Model using SD v1.4
- To make similar images with the train data
    - Extracting Caption with pre-trained DeepFace model (CNN-based; local) and ViT (transformer-based; global)
    - Prompt to DeepFace: The {gender} is {age} years old {race} and {emotion}
    - Combining two Captions: ‘A face image of {caption from ViT}. The final prompt was ‘And the {gender} is {age} years old {race} and {emotion}.’
    - Calculate VGG-19 Gram matrix–based style similarity, compare with the threshold, and guide the model to be more similiar with the real images

## Detector Strategy
- Detection Model using ViT
    - input: 224 x 224, patch: 16 x 16
    - LoRA to attention query and key
    - Loss: Single Center Loss
        - set a center of real image features
        - goal: real becomes to be close from the center and fake to be far from the center
        - less-sensitive to the type of fake images (GAN/diffusion-based)

### Notice
- I removed all image dataset, because of the capacity issues
- The dataset is from kaggle. 
    - [Thread for real faces dataset] (https://www.kaggle.com/c/deepfake-detection-challenge/discussion/122786)
    - [1 Million Fake Faces] (https://www.kaggle.com/c/deepfake-detection-challenge/discussion/121173)
- We also used the next two related works for some trials
    - [Fairness-Generalization] (https://github.com/Purdue-M2/Fairness-Generalization)
    - [VLM-Detect] (https://github.com/Mamadou-Keita/VLM-DETECT)