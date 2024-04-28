# Build_Custom_GPT
Building a Decoder based pre-trained Transformer from scratch, based on the landmark paper "Attention Is All You Need" (https://arxiv.org/pdf/1706.03762), which can be trained on any given text Dataset.

The idea is not to replicate gpt 3.5 because that is certainly not possible to achieve with limited processing resources we have, rather to built the underlying decoder only Transformer architecture proposed in the mentioned paper, which is infact forms the core of the GPT. 

Train Data - We have trained our Language model on a subset of "tiny story data" which is a collection of short English stories. For Training, we took a set of 6000 stories comprises of around 5 M characters.

Model Size - The trained model is of 6M parameters. The model is trained on free T4 GPU available on Google colab. We could train add more layers, use higher embedding size, batch size, context length and train a model of much bigger size, however this would require a more resourceful GPU, something like A100 GPU.

Some Insights for the Hyper Paramters Used - 

batch_size = 64         # Independent sequences to process in parallel

block_size = 128        # Size of each independent sequence

learning_rate = 1e-5

n_embd = 256           # Token embedding size

pos_emb = 256          # Position Embedding Size

n_head = 8             # Number of head in Multi Head Attention Layer

n_layer = 8            # Number of Sequential Blocks

dropout = 0.1  

Training and Validation Loss 
This model is trained on a character level token size comprising of 8-layer Transformer with 8 heads in each layer. On T4 GPU, the training run takes about 60 minutes and the best train loss and validation loss we got after 15000 iterations are 0.8352 and 0.8410 respectively.

Dependencies:
pytorch
datasets for huggingface datasets

Example Inference from the Trained model - 

<img width="1147" alt="Screenshot 2024-04-29 at 12 47 44 AM" src="https://github.com/Suraj-Jena/Build_Custom_GPT/assets/35285637/1b8181bf-8b78-41c2-84e8-3e6efd4a5558">









I know at this moment this does not make that much sense, but it is still a good start for a character-level model as small as 6M parameters for just 60 minutes on a limited resource GPU. However we can definitely obtain better results with training a larger model and by doing specific finetuning on this pre-trained model.

