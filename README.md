# vllm-coco-captioner
Local vLLM setup for generating image captions from COCO images and storing them in a database.
Project Overview

The system processes COCO dataset images and automatically generates captions using a vision-language model. The generated outputs are stored in a structured SQLite database.
It uses vLLM to run a multimodal model efficiently.

How It Works.  

1.Environment Setup
Set up a local environment with vLLM to run the vision model fast because vLLM utilizes     PagedAttention, a memory management technique that significantly reduces memory waste accelerates inference.
2.Model Initialization
Load a vision-language model (Qwen2-VL) that can understand images, not just text.
3.Image-to-Text Generation
Each COCO image is passed to the model, which generates a descriptive caption.
4.Database Storage
The generated caption is saved into a SQLite database along with the image ID and link.

In this project i used VLM because it  can interpret both images and language.A standard LLM can only process text.We are working with both images and text  VLMs are the correct fit.

Qwen2-VL-2B
________________________________________________________________________

 I chose the Qwen2-VL model. Larger models like Qwen2-VL-7B or Llama Vision could work too, but they need much more GPU and are not optimal for standard Colab. The 2B model fits perfectly in a standard Colab T4 GPU.
____________________________________________________________________________

SQLite is used because it is serverless and lightweight. It creates a local .db file that is easy to export, which is perfect for a Colab environment compared to setting up a heavy MySQL server."
Results example
The captioning pipeline successfully generated and stored textual descriptions for the selected COCO images using the Qwen2-VL-2B model running under vLLM.
