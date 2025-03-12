---
layout: single
title: "Quantization"
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
1. Post-Training Quantization (PTQ)

