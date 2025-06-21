# AI - Deepfake Detection
- This project aims at Deepfake Detection.  
- Therefore, two models are needed to generate fake images and distinguish fake images.  
- We generated fake images using **stable diffusion**, and created a detection model using **Lora and single center loss**.  

## Notice
- I removed all image dataset, because of the capacity issues
- The dataset is from kaggle. (Sorry I can't find the link now)
- We also used the next two related works
    - [Fairness-Generalization] (https://github.com/Purdue-M2/Fairness-Generalization)
    - [VLM-Detect] (https://github.com/Mamadou-Keita/VLM-DETECT)