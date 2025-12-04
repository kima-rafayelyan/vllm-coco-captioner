# COCO Image Captioning with vLLM & Qwen2-VL

This project performs automatic caption generation for COCO dataset images using a multimodal vision-language model. The generated captions are stored in a structured SQLite database for easy retrieval and evaluation. The system runs efficiently with **vLLM**, enabling fast inference even on a standard Colab T4 GPU.

---

## 🚀 Project Overview

The pipeline processes COCO images and produces human-like text descriptions using Qwen2-VL.  
Unlike standard LLMs that can only process text, a Vision-Language Model (VLM) interprets both **visual input + natural language**, making it the correct architecture for this task.

---

## 🔧 How It Works

### 1. Environment Setup
A local inference environment is configured with **vLLM**, which uses **PagedAttention** to reduce GPU memory waste and accelerate generation. This allows smooth execution on limited-memory GPUs such as **T4**.

### 2. Model Initialization
A multimodal model (**Qwen2-VL-2B**) is loaded.  
This model can understand images directly, extract high-level semantics, and convert them into text.

### 3. Image-to-Text Generation
Each COCO image is passed to the model, and a descriptive caption is automatically generated for it.

### 4. Database Storage
Captions are saved into a **SQLite** database containing:
- Image ID
- COCO image path/link
- Generated caption

This ensures easy query, comparison, and further evaluation.

---

## 🧠 Why Qwen2-VL-2B?

Qwen2-VL is a multimodal model capable of processing both images and language, making it ideal for captioning tasks.  
While larger options such as **Qwen2-VL-7B** or **Llama-Vision** provide more parameters, they require significantly more GPU memory, making them impractical for Colab.

**Qwen2-VL-2B advantages:**
- Multimodal (vision + text)
- Fits comfortably on **T4 GPU**
- Provides fast inference under **vLLM**
- Lightweight yet accurate for captioning tasks

---

## 🗄️ Why SQLite?

SQLite is chosen because it:
- Is **serverless and lightweight**
- Generates a simple local `.db` file
- Requires zero configuration or deployment
- Is ideal for Colab compared to running MySQL/PostgreSQL

This makes experiment tracking and caption export simple and efficient.

---

## 📊 Results

The system successfully:
- Generated coherent captions for COCO images
- Stored them in a structured SQLite database
- Operated efficiently using **Qwen2-VL-2B** with **vLLM** on a T4 GPU

Example output:
