# Digital Humans - Team 7: Text-to-Image Generation Research

A comprehensive research project exploring advanced text-to-image generation techniques using DreamBooth and novel Image2Dream methodology for personalized image synthesis.

## Overview

This repository contains the implementation and experimental results for our Digital Humans course project, focusing on personalized text-to-image generation. We explore two main approaches:

1. **DreamBooth Fine-tuning**: Traditional and LoRA-based fine-tuning of Stable Diffusion models
2. **Image2Dream**: A novel approach for learning personalized embeddings from image collections

## Key Features

- **Multiple DreamBooth Implementations**: Support for both traditional and LoRA-based fine-tuning
- **Image2Dream Pipeline**: Custom projection model for mapping CLIP image embeddings to Stable Diffusion text space
- **Comprehensive Experiments**: Systematic evaluation across different datasets and hyperparameters
- **Ready-to-Use Notebooks**: Kaggle-compatible notebooks for easy experimentation

## Repository Structure

```
Digital_Humans_team_7/
├── notebooks/
│   ├── dreambooth-single-use.ipynb           # Basic DreamBooth fine-tuning
│   ├── dreambooth-lora-single-use.ipynb      # LoRA-based DreamBooth
│   ├── dreambooth-lora-experiments.ipynb     # Comprehensive parameter study
│   └── image2dream.ipynb                     # Image2Dream implementation
├── outputs/                                  # Generated images and results
├── report.pdf                               # Detailed research report
├── LICENSE                                  # MIT License
└── README.md                               # This file
```

## Methods

### DreamBooth Fine-tuning

DreamBooth enables personalization of text-to-image diffusion models using just 3-5 images of a subject. We implement:

- **Traditional DreamBooth**: Full model fine-tuning with prior preservation
- **DreamBooth + LoRA**: Parameter-efficient fine-tuning using Low-Rank Adaptation
- **Hyperparameter Optimization**: Systematic study of learning rates, training steps, and dataset sizes

### Image2Dream

Our novel approach that learns to map collections of images to personalized text embeddings:

1. **Projection Learning**: Train a neural network to map CLIP image embeddings to Stable Diffusion text space
2. **Embedding Aggregation**: Experiment with different pooling strategies (mean, median, quantiles) to combine multiple image embeddings
3. **Distance Metrics**: Evaluate cosine similarity, Euclidean, and Manhattan distance for optimal embedding selection

## Datasets

We evaluate our methods on diverse datasets:

- **Calico Cats**: [5 images](https://www.kaggle.com/datasets/defne1818/calico-cat) | [25 images](https://www.kaggle.com/datasets/defne1818/calico-25)
- **Golden Retrievers**: [Dog breed dataset](https://www.kaggle.com/datasets/eward96/dog-breed-images)
- **Pugs**: [Dog breed dataset](https://www.kaggle.com/datasets/eward96/dog-breed-images)
- **Human Faces**: [FaceScrub dataset](https://www.kaggle.com/datasets/rajnishe/facescrub-full)

## Setup and Usage

### Prerequisites

- Python 3.8+
- CUDA-compatible GPU (recommended)
- Hugging Face account and token
- Weights & Biases account (for experiment tracking)

### Quick Start

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/Digital_Humans_team_7.git
   cd Digital_Humans_team_7
   ```

2. **Set up credentials**:
   - Create a Hugging Face token: https://huggingface.co/settings/tokens
   - Create a W&B API key: https://wandb.ai/authorize

3. **Run experiments**:
   - Upload notebooks to Kaggle or your preferred environment (with a GPU)
   - Update credential placeholders in the notebooks
   - Select your dataset and run the cells

### Notebook Descriptions

| Notebook | Description | Use Case |
|----------|-------------|----------|
| `dreambooth-single-use.ipynb` | Basic DreamBooth implementation | Quick prototyping |
| `dreambooth-lora-single-use.ipynb` | LoRA-based fine-tuning | Memory-efficient training |
| `dreambooth-lora-experiments.ipynb` | Comprehensive parameter study | Research and optimization |
| `image2dream.ipynb` | Image2Dream pipeline | Novel embedding approach |

### Configuration Requirements

#### DreamBooth Single Use (`dreambooth-single-use.ipynb`)

| Variable | Description | Example Value |
|----------|-------------|---------------|
| `new_token` | Custom token identifier | `"[V]"` |
| Dataset path | Path to your training images | `"/kaggle/input/calico-cat/"` |
| `instance_prompt` | Training prompt template | `"a photo of [V] cat"` |

#### DreamBooth LoRA Single Use (`dreambooth-lora-single-use.ipynb`)

**Required Setup:**
- Hugging Face token
- Weights & Biases API key

| Variable | Description | Example Value |
|----------|-------------|---------------|
| `YOUR_HUGGING_FACE_TOKEN` | HF authentication token | `"hf_xxxxxxxxxxxxx"` |
| `YOUR_WANDB_KEY` | W&B API key for logging | `"xxxxxxxxxxxxxxx"` |
| `YOUR_HF_ACCOUNT_NAME` | Your HF username | `"yourusername"` |
| `new_token` | Custom token identifier | `"[V]"` |
| Dataset path | Path to your training images | `"/kaggle/input/calico-cat"` |
| `instance_prompt` | Training prompt template | `"a photo of [V] cat"` |

#### DreamBooth LoRA Experiments (`dreambooth-lora-experiments.ipynb`)

**Required Setup:**
- Hugging Face token  
- Weights & Biases API key

| Variable | Description | Example Value |
|----------|-------------|---------------|
| `[YOUR_HF_TOKEN]` | HF authentication token | `"hf_xxxxxxxxxxxxx"` |
| `[YOUR_W&B_API_KEY]` | W&B API key for logging | `"xxxxxxxxxxxxxxx"` |
| `datasets` dict | Dataset configurations | See notebook for structure |
| `nr_images_list` | Number of training images | `[5, 30, 70]` |
| `nr_class_images_list` | Number of class images | `[5, 30, 70]` |
| `lr` | Learning rates to test | `[2e-6, 5e-6]` |

#### Image2Dream (`image2dream.ipynb`)

**Important:** Remember to modify dataset path and animal variable based on your chosen dataset.

| Variable | Description | Example Values |
|----------|-------------|----------------|
| `DATA_PATH` | Path to your image dataset | `"/kaggle/input/dog-breed-images/pug"` |
| | | `"/kaggle/input/dog-breed-images/golden_retriever"` |
| | | `"/kaggle/input/calico-25"` |
| | | `"/kaggle/input/calico-cat"` |
| `animal` | Type of animal in dataset | `"dog"` (for pug/golden retriever) |
| | | `"cat"` (for calico datasets) |
| `new_token` | Custom token identifier | `"[V]"` |
| `N_EPOCHS` | Training epochs for projection | `2000` |

## Results

Detailed results and analysis are available in our [research report](report.pdf).

## Generated Examples

The `outputs/` directory contains sample generations across different methods and datasets, showcasing the quality and diversity of our approaches.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Citation

If you use this work in your research, please cite our report:

```bibtex
@techreport{digital_humans_team7_2025,
  title={Text-to-Image Generation with DreamBooth and Image2Dream},
  author={Defne Kurtulus, Edoardo Negri,Aaron Achermann},
  year={2025},
  institution={ETH}
}
```

## Contact

For questions about this research, please refer to our detailed [report](report.pdf) or open an issue in this repository.
