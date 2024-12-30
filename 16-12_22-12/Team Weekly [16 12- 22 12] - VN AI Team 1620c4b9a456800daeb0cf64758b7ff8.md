# Team Weekly [16.12- 22.12] - VN AI Team

Created: December 20, 2024 4:16 PM

# Work Summary:

## 1. Image Colorization

### Reference-based Colorization: Color Blending on Mobile

- **Model**: Color Blending (DDColor + ConvNeXt-Ref)
- **Device**: Redmi K70 Pro
- **Framework:** Onnx Runtime
- **Inference Time**: 710ms/frame, ~8.5s for 150 frames (with Transfer Color)
- **Memory Usage**: 612MB for image, 750MB for video

**Some Results:** from top to bottom: Input grayscale, Day background as a reference → Colorized result

![f4ea173b-42db-4388-9d52-362782829004.jpg](f4ea173b-42db-4388-9d52-362782829004.jpg)

![620a0ada-6733-4aac-8136-f6d53902131a.jpg](620a0ada-6733-4aac-8136-f6d53902131a.jpg)

![image.png](image.png)

### Mobile SDK: Integrate Low Light and Colorization

![llie+colorization.jpg](lliecolorization.jpg)

**Discussion:**

- The inference time is relatively high → retrain the model to reduce the inference time.
- Day background and night alignment is a challenging task → project next phase.

## 2. Infant Crying Detection

### First Demo on T31 board:

- **ISSUE : incorrect model inference → ON PROGRESS**

![image.png](image%201.png)

![image.png](c6142db8-f7ab-4b01-8ec1-e44b33120c0f.png)

![image.png](image%202.png)

- **Audio processing Pipeline Alignment**

![image.png](image%203.png)

![image.png](image%204.png)

![image.png](image%205.png)

**8-bit quantized model test:**

![image.png](image%206.png)

**4-bit quantized model test:**

![image.png](image%207.png)

### Fine-tuned Model:

Wait for the latest Pipeline Alignment

**Perspective:**

- Fine-Tune Post-Processing for Noise Types
    - Given that baby-related and low-amplitude noises are significant sources of FAR,  applying **post-processing filters** that reduce sensitivity specifically for these noise categories.
- Consider Higher Precision
    - **4-bit quantization** may be too aggressive, leading to loss of important information and increasing FAR. Using **8-bit quantization** instead can help retain more precision and potentially provide a more reliable balance between Sensibility and FAR in case that 4-bit model is still too overfitting after fine tuning parameters
        
        **→ checked but still encountering the model inference issues**
        

### Issue:

# Next Week's Work Plan:

## 1. Image Colorization

| **Start Date** | **Finish Date** | **Duration** | **Milestone** | **Description** | **Target** |
| --- | --- | --- | --- | --- | --- |
| Dec 23rd | Dec 29th | 1 week | Reference-based Colorization: Deployment | ** Retrain some light weight models to reduce inference time and mem usage | ** Reduce inference time and keep quality close to the current pipeline |

## 2. Infant Crying Detection

| **Start Date** | **Finish Date** | **Duration** | **Milestone** | **Description** | **Target** |
| --- | --- | --- | --- | --- | --- |
| Dec 23rd | Dec 29th | 1 week |  | **Debugging on the T31 board side |  |

# Project Progress:

## 1. Image Colorization

- Done: Automatic and Reference-based demo.
- In progress: Color Blending demo.
- Target: Fully functional Automatic, Reference-based, Color Blending on mobile.

| **Start Date** | **Finish Date** | **Duration** | **Milestone** | **Description** | **Target** |
| --- | --- | --- | --- | --- | --- |
| Dec 2nd | Dec 8th | 1 week | Reference-based Colorization: Improve baseline model | ** Improve the reference-based method | ** The improved version of the baseline. |
| Dec 9th | Dec 15th | 1 week | Reference-based Colorization: Deployment | ** Deploy the first version of Reference-based Colorization on mobile | ** First demo of Reference-based Colorization on mobile |
| Dec 16th | Dec 22nd | 1 week | Reference-based Colorization: Deployment | ** Convert Color Blending pipeline to C++ on mobile | ** Color Blending demo on mobile |
| **Dec 23rd** | **Dec 29th** | **1 week** | **Reference-based Colorization: Deployment** | **** Refine and optimize the model on mobile if any issues arise** | **** The improved version of the model on mobile** |

## 2. Infant Crying Detection

- On progress of deploying model

| **Start Date** | **Finish Date** | **Duration** | **Milestone** | **Description** | **Target** |
| --- | --- | --- | --- | --- | --- |
| Dec 2nd | Dec 8th | 1 week | 1st demo on T31 board —> optimizing the board | **Collab with embedded team for testing proposed model. **Receive feedback to modify the model (if having any). **Fine-tune the model to require accuracy | ** first demo on T31 board |
| Dec 9th | Dec 15th | 1 week | Measure the optimized model performance | **Collab with embedded team for deploying model on T31. **Post processing for handling “alarm fatigue” | ** The result of optimized model and post processing part  |
| Dec 16th | Dec 22nd | 1 week |  | **Debugging on the T31 board side |  |
| **Dec 23rd** | **Dec 29th** | **1 week** |  | ****Debugging on the T31 board side** |  |