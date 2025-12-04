## vllm-coco-captioner

Local vLLM setup for generating image captions from COCO images and storing them in a database.



## 🚀 Project Overview

The system processes COCO dataset images and automatically generates captions using a vision-language model. The generated outputs are stored in a structured SQLite database.
It uses vLLM to run a multimodal model efficiently.




## 🔧 How It Works

### 1. Environment Setup
Set up a local environment with vLLM to run the vision model fast because vLLM utilizes  **PagedAttention**, a memory management technique that significantly reduces memory waste accelerates inference. This allows smooth execution on limited-memory GPUs such as **T4**.

### 2. Model Initialization
Load a vision-language model (**Qwen2-VL**) that can understand images, not just text.

### 3. Image-to-Text Generation
Each COCO image is passed to the model, and a descriptive caption is automatically generated for it.

### 4. Database Storage
Captions are saved into a **SQLite** database containing:
- Image ID
- COCO image link
- Generated caption



In this project i used **VLM** because it  can interpret both images and language.A standard LLM can only process text.We are working with both images and text  VLMs are the correct fit.


## 🧠 Why Qwen2-VL-2B?

Qwen2-VL is a multimodal model capable of processing both images and language. Larger models like Qwen2-VL-7B or Llama Vision could work too, but they need much more GPU and are not optimal for standard Colab. The 2B model fits perfectly in a standard Colab T4 GPU.



## 🗄️ Why SQLite?

SQLite is used because it is serverless and lightweight.
It creates a local .db file that is easy to export,
which is perfect for a Colab environment compared to setting up a heavy MySQL server."



## 📊 Results
The system successfully:
- Generated coherent captions for COCO images
- Stored them in a structured SQLite database
- Operated efficiently using **Qwen2-VL-2B** with **vLLM** on a T4 GPU



| **A woman in a red jacket and black pants is skiing down a snowy slope, holding ski poles and wearing goggles.** |
| :---: |
<img width="645" height="430" alt="Screenshot from 2025-12-04 02-42-22" src="https://github.com/user-attachments/assets/567d4009-c100-41de-8dfa-4d5b3c9bf2c5" />


| **A blue bicycle is parked on a sidewalk next to a street, with a white van and several other vehicles visible in the background.** |
| :---: 
|<img width="645" height="390" alt="Screenshot from 2025-12-04 02-41-44" src="https://github.com/user-attachments/assets/696de92d-fdb3-49e6-a40e-73b940423804" />


| **A person is standing in a kitchen, wearing an apron, and pointing at a table with dough and other kitchen items. The kitchen is equipped with various cooking utensils and appliances, including a stove, sink, and oven. ** |
| :---: |
<img width="645" height="430" alt="Screenshot from 2025-12-04 02-42-32" src="https://github.com/user-attachments/assets/14c96df2-c15a-48b1-a609-b0d66951b2ba" />


