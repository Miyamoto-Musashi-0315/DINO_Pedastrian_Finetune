# DINO-based Object Detection Project

This project uses the DINO (DETR with Improved DeNoising Anchor Boxes) model for object detection, with modifications for a specific use case. The code is based on the [IDEA-Research/DINO](https://github.com/IDEA-Research/DINO) repository.

## Setup

1. Clone the DINO repository:
   ```
   git clone https://github.com/IDEA-Research/DINO.git
   ```

2. Install the required dependencies:
   - Follow the installation instructions in the [IDEA-Research/DINO](https://github.com/IDEA-Research/DINO) repository.
   - Download the `requirements.txt` file and install the dependencies.

3. Modify the following files:
   - `DINO_4scale.py`
   - `engine.py`
   - `slconfig.py`
   - `main.py`
   - Update the numpy part from float to float64 inside the `/usr` folder (Colab implementation)
   - Seperate `json` to `json_val` and `json_train` [Follow the IPYNB for more detailed implementation] 

## Pre-trained Model

Download the DINO checkpoint for evaluation:
- URL: [https://drive.google.com/drive/folders/1qD5m1NmK0kjE5hh-G17XUX751WsEG-h_](https://drive.google.com/drive/folders/1qD5m1NmK0kjE5hh-G17XUX751WsEG-h_)
- File: `checkpoint0033_4scale.pth` (DINO-4scale trained on 12 epoch with ResNet-50 backbone)

## Evaluation

To evaluate the model, use the following command:

```bash
bash scripts/DINO_eval.sh /path/to/data /path/to/checkpoint.pth
```

Example:
```bash
bash scripts/DINO_eval.sh /content/drive/MyDrive/dino /content/drive/MyDrive/dino/Copy_of_checkpoint0033_4scale.pth
```

## Experiments

Two experiments were conducted by modifying values in `DINO_4scale.py`:

### Experiment 1
- num_classes: 2
- learning rate: 0.0001
- epochs: 12
- batch size: 2
- dropout: 0.0

### Experiment 2
- num_classes: 2
- learning rate: 0.0001
- epochs: 10
- batch size: 2
- dropout: 0.1

The first experiment achieved a higher Average Precision (AP).

## Fine-tuned Model

Download the fine-tuned checkpoint:
- URL: [https://drive.google.com/file/d/1RqRO-MCJXiiMypEwEGUpYjics_N_rsfW/view?usp=drive_link](https://drive.google.com/file/d/1RqRO-MCJXiiMypEwEGUpYjics_N_rsfW/view?usp=drive_link)

To test the fine-tuned model on the validation set, use the same evaluation command as before, but replace the checkpoint path with the path to the fine-tuned model.

## Additional Information

For more detailed information on how the code works, please refer to the IPYNB file in the repository and for detailed report on experiment go through the - `report.pdf`

