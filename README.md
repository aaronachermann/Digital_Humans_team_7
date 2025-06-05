# Digital_Humans_team_7

## Image datasets

- calico cat (5 images): https://www.kaggle.com/datasets/defne1818/calico-cat
- calico cat (25 images): https://www.kaggle.com/datasets/defne1818/calico-25
- golden retriever images used with Image2Dream model: [https://www.kaggle.com/datasets/eward96/dog-breed-images](https://www.kaggle.com/datasets/eward96/dog-breed-images?select=golden_retriever)
- pug images used with Image2Dream model: https://www.kaggle.com/datasets/eward96/dog-breed-images?select=pug



-Image2Dream:  modifica dataset, e variabile animal

https://www.kaggle.com/code/edoardonegri/image2dream




lora:
user should create Huggin Face token and W&B API KEY:

"""
# Use your Hugging Face token for login
login(token="[YOUR_HF_TOKEN]")

# Set the W&B configuration via environment variables
os.environ["WANDB_MODE"] = "online"  
os.environ["WANDB_API_KEY"] = "[YOUR_W&B_API_KEY]"  # Replace with your W&B API key 
"""

dataset 1: https://www.kaggle.com/datasets/khushikhushikhushi/dog-breed-image-dataset  -> folder /Golden_Retriever
dataset 2: https://www.kaggle.com/datasets/rajnishe/facescrub-full -> folder /Bill_Cosby
