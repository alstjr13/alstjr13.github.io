---
layout: single
title: "[Deep Learning] Quantization"
categories: ['ML & DL']
tag: [Data, ['Machine Learning'], ['Deep Learning']]
toc: true
---

#### What is Quantization in Deep Learning?
**Quantization** in deep learning refers to the **process of approximating a model's parameters (weights and activations)** using lower-precision data types.

In simple terms, quantization refers to the process of changing floating-point type to integer (or fixed point) type parameters.

#### Why use Quantization in Deep Learning?
The need for quantization arises from the growing demand to deploy deep learning models on devices with limited hardware resources (i.e. 하드웨어 기술의 발전이 비교적 소프트웨어의 발전보단 느리다보니, 소프트웨어의 발전과 함께 경량화하여 상용화 시키는 편이 낫다는 판단)

We employ quantization for:
1. **Reduced Memory Footprint**: FP32 (Float-point 32) requires 32 bits, while INT8 takes up 8 bits of memory. Using INT8 instead of FP32 reduces the use of memory and it is crucial for deploying models on devices with limited storage capacity.
2. **Faster Inference**: Quantized models require fewer computations (Arithmetic processes in INT8 is generally faster than FP32). It is especially faster on hardware that supports integer arithmetic or specialized accelerator like TPUs or NVIDIA Tensor cores.
3. **Lower Power Consumption**: With the rise of technologies (hardware and software), quantization significantly reduces the energy required for inferences, which is crucial for battery-operated devices like wearables, mobile phones or IoT devices.
4. **Edge Device Deployment**: With quantized models, high-performance deep learning models can be deployed on edge devices without heavily relying on cloud-based inference.

#### Types of Quantization

##### 1. **Post-Training Quantization (PTQ)**
Post-Training Quantization is applied after the model has been trained using 32-bit precision. No retraining is required, which makes this technique is easy to apply. The model's weights and activations are converted from FP32 to lower precision formats like INT8.

PTQ can be divided into $3$ common types:
- **Dynamic Quantization**: 
  - Quantizes only the weights to INT8 and keeps activations in FP32 during inference
  - During inference, the activations are dynamically quantized based on their range of values
  - (한국어로) training 이후, 모델 weight들을 quantization 진행
  - activation때는 FP32 형태로 저장해놓고, inference 할 때 quantize하고, 완료 후 다시 dequantize해서 저장
- **Static Quantization (Full Integer Quantization)**:
  - Both weights and activations are quantized to INT8
  - Requires calibrating using sample dataset to estimate the dynamic range of activations before deployment
  - (한국어로) weight 와 activation 모두 INT8로 quantized
  - 
- **Float16 quantization**:
  - Instead of quantizing to INT8, this method quantizes weights and activations to FP16, which maintains some of the dynamic range of FP32 while providing faster inference

##### 2. **Quantization-Aware Training (QAT)**
Quantization Aware Training is more sophisticated where quantization is simulated during the training process. In QAT, the model learns to adapt its weights to lower-precision format, which results in less accuracy degradation compared to PTQ.

The model is trained with fake quantization, where FP32 values are rounded to low-precisions during forward passes, but gradients and updates remain in FP32. Since the model is "aware of the quantization process during training", it can compensate for reduced precision, leading to better performance after quantization.

#### Techniques in Quantization

##### Uniform Quantization
- The entire range of floating-point values is divided into equal intervals, and each interval is represented by a quantized value. This involves mapping values from the floating-point domain to the integer domain using a scaling factor and an offset (a.k.a. zero-point or quantization bias).

<img src="/assets/files/pictures/uniform-quantization.png" width="30%" height="30%" style="border:none;">

##### Non-Uniform Quantization
- Divides the floating-point values into unequal intervals (range into intervals of unequal size)
  - Giving more representation to values that occur frequently **or** critical to model's performance
- **Useful in cases where** certain regions of the weight distribution need higher precision than others

<img src="/assets/files/pictures/non-uniform-quantization.png" width="30%" height="30%" style="border:none;">

##### Min-Max Quantization
- Uses minimum and maximum values of the weights or activations to define the range for quantization.
- Then, values are linearly scaled into the integer domain based on the given range

<img src="/assets/files/pictures/minmax-quantization.png" width="30%" height="30%" style="border:none;">

##### Logarithmic Quantization
- Values are quantized based on a logarithmic scale (provides better precision for small and large values).
- **Useful in cases where** the model parameters vary significantly in magnitude.

<img src="/assets/files/pictures/logarithmic-quantization.png" width="30%" height="30%" style="border:none;">

#### Journals to consider about Quantization
- [A Survey of Quantization Methods for Efficient Neural Network Inference](https://arxiv.org/pdf/2103.13630)
- [A White Paper on Neural Network Quantization](https://arxiv.org/pdf/2106.08295)
