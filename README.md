# Introduction
This repo contains the implementation of predicting gene expression levels of random promoter sequences by a large temporal convolutional networks-based language model, namely DNA-TCN. The implementaion provides data preprocessing, data loaders, model building and training. The character-level Temporal Convolutional Network (TCN) described in [(Bai, Kolter, and
Koltun 2018)](https://api.semanticscholar.org/CorpusID:4747877) is adopted.

# Cite
```
@article{dna-tcn2023,
  title={Predicting gene expression levels of random promoter sequences by a large temporal convolutional networks-based language model},
  author={Alsaggaf, Ibrahim and Barton, Carl and Wan, Cen},
  note={Submitted for publication to AAAI 2024: LLMs4Bio conference, November 2023}
}
```

# Usage
The impelementation is customised to run on a TPU virtual machine (tpu-vm) with PyTorch/XLA, it was tested on a tpu-vm v2-8 with Pytorch version 1.11. To run this impelementation on GCP yon need to do the following steps:

1\. Create a tpu-vm instance with Pytorch version 1.11 installed

`gcloud compute tpus tpu-vm create [INSTANCE NAME]
--zone=[SELECTED ZONE]
--accelerator-type=v2-8
--version=tpu-vm-pt-1.11`

2\. SSH to the tpu-vm instance

`gcloud compute tpus tpu-vm ssh [INSTANCE NAME]
  --zone [SELECTED ZONE]`
  
3\. Install dependencies using the given `requirements.txt` file

`pip3 install -r requirements.txt`

4\. Copy the dataset and the code from your GCP bucket to the instance

`gsutil -m cp gs://[BUCKET NAKE]/[FOLDER NAME]/* .`

Assuming all required files are in a single folder.

5\. Run `train.py` to train the model using all train sequences.

`python3 train.py`

`train.py` contains data preprocessing and model training, for data preprocessing details please see the report.

# Acknowledgements
We thank DREAM Challenges for organizing this competition, and Google Research for providing TPU resources to make training the model possible. We also acknowledge the support by the School of Computing and Mathematical Sciences, and the Birkbeck GTA programme.
