# <img style="float: left;" src="assets/logo.png" width="40" /> &nbsp; SCYCLONE | AI

**Scyclone AI** GitHub repository is an extension to the main [Scyclone](https://github.com/Torsion-Audio/Scyclone) repository. Scyclone is an audio plugin that utilizes **neural timbre transfer** technology to offer a new approach to audio production. The plugin builds upon [RAVE](https://github.com/acids-ircam/RAVE) methodology, a realtime audio variational auto encoder, facilitating neural timbre transfer in both single and couple inference mode. <br /><br />This repository contains a comprehensive step-by-step instruction that will guide you through the process of creating your own custom sounding presets. You can use both the Colab notebooks or command line to train models.





## Colab

If you are new to machine learning, we encourage you to start with this notebook.
There we have compiled all the necessary information and instructions to begin creating your custom sounding Scyclone presets.

[![colab_badge](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1xKsaGDMWY1NRhP0ndD-iVg89O57GdZdz?usp=sharing) 

If you hold former AI model training knowledge and want to use a notebook to train your custom sounding Scyclone preset, start with this notebook. All parameters and configurations are compiled and set to train, export and start using the models inside Scyclone. 

[![colab_badge](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1DU9KvMdYTOcTT8eYundZ2wruetNDtpX0?usp=sharing) 




## Installation

Scyclone uses RAVE as the timbre tranfer engine. to install RAVE, create a new virtual environment, activate it and run:

```bash
pip install acids-rave
```

Install **ffmpeg**:

```bash
conda install ffmpeg
```


## Data Preprocessing
RAVE's original preprocessing code accepts various file extentions. To preprocess your data, run the script:
```bash
rave preprocess --input_path /path/to/audio --output_path /dataset/path --sampling_rate 48000
```


## Training

In our experiments we used **v1** of RAVE with specific configurations, making the model suitable for the plugin's environment. Please note that configurations other than those mentioned below may lead to undesirable outcome or cause harm to the export process.

```bash
rave train --config v1 --config centered --db_path /dataset/path --name training_name --override LATENT_SIZE=16 --override CAPACITY=32 
```

## Export

Once the training is finished, used the script below to export your preset.

```bash
rave export_onnx --run /path/to/run
```


## Usage

Once you have the trained model exported, you are ready to use it as a preset inside **Scyclone**. 

- Save the model to your local drive 
- Open the application 
- Hover over one of the network nodes in order for the network arm to appear. 
- Click on the load model icon and load the preset.

![interface](assets/load_model.png)
