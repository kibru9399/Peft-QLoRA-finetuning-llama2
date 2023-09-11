# Peft-QLoRA-finetuning-llama2
## **Project Overview**

This project fine-tuned the Llama2 7B parameter model on the Billsum dataset using a small computing resource(1 FREE COLLAB T4 GPU) for the task of text summarization. The model was trained using Qlora and PEFT techniques, and the positional embedding of the RoPE was modified to be able to handle more tokens than the default.

## **Dataset**

The Billsum dataset is a collection of senate bills from the United States Congress. The dataset contains over 100,000 bills, and each bill is associated with a summary. The summaries are written by human experts, and they provide a concise overview of the bill.

## **Model**

The Llama2 7B model is a large language model that was developed by meta The model has 7B parameters, and it is trained on a massive dataset of text and code. The model was fine-tuned on the Billsum dataset using Qlora and PEFT techniques.

## Model Modifications

The model uses the RoPE positional embedding, which allows the model to handle longer sequences than the default sinusoidal positional embedding. However, the llama2 RoPE embedding has a fixed maximum position of 4096, which limits the length of the input. To overcome this limitation, I modified the RoPE embedding initialization function to scale the base parameter according to the formula proposed in NTK Scaling. This allows the RoPE embedding to handle more than 4096 positions without increasing the perplexity. However, due to memory constraints, I left the maximum position to default.

## **Code**

The script for this project is available above. Jupyter notebook is included to run the script and pass the model hyperparameters as cl arguments.

## **Limitations**

The main limitation of this project is compute power. A shorter version of the dataset, the ‘summary’, column is used as an input becuase using the full bill was impossible due to GPU ram shortage. hence, better performance could be acheived by increasing the context length to be able to handle the full bill at once, and increasing the GPU to handle the size of dataset would improve the model much better.
