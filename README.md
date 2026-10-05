# Machine Learning 2

Three coursework assignments covering neural networks, computer vision, text emotion classification, and generative models. The notebooks include the implementations, written derivations, experiment discussions, and saved plots; PDF reports provide a read-only version of the submissions.

## Assignments

| Assignment | Topics | Files |
| --- | --- | --- |
| **HW1 — Neural networks and computer vision** | Softmax and cross-entropy derivatives; manual backpropagation for an MNIST classifier; a grocery-image CNN; VGG16 filter analysis. | [Notebook](HW1/neural-networks-and-computer-vision.ipynb) · [Report](HW1/report.pdf) |
| **HW2 — Text emotion classification** | Generalization and overfitting; tweet preprocessing; vanilla RNN and LSTM classifiers for happiness, sadness, and neutral text; optimizer and regularization comparisons. | [Notebook](HW2/text-emotion-classification.ipynb) · [Report](HW2/report.pdf) |
| **HW3 — Face generation with GANs** | A convolutional generator and discriminator trained on CelebA; generated-image grids; training losses; latent-space experiments. | [Notebook](HW3/face-generation-gan.ipynb) · [Report](HW3/report.pdf) |

To browse the work, open a notebook or report above. The saved outputs can be viewed without installing dependencies or downloading datasets.

## Local setup

Use Python 3.10 or 3.11 in a dedicated virtual environment. The requirements retain the original PyTorch 2.1.2 / torchvision 0.16.2 pairing; they are a focused dependency list, not a complete lockfile of the original environment.

```sh
git clone https://github.com/omri-lazover/Machine-Learning-2.git
cd Machine-Learning-2
python -m venv .venv
```

Activate the environment:

```powershell
# Windows PowerShell
.venv\Scripts\Activate.ps1
```

```sh
# macOS / Linux
source .venv/bin/activate
```

Install the dependencies and launch JupyterLab:

```sh
python -m pip install -r requirements.txt
python -m jupyter lab
```

Open the notebook inside its assignment folder and use that folder as the kernel's working directory. Run the relevant setup cells before training or evaluation. Training can take substantial time; the notebooks use CUDA where available.

## Data and checkpoints

| Assignment | Included | Additional files needed to rerun |
| --- | --- | --- |
| **HW1** | Notebook and report. | MNIST downloads automatically. The CNN section expects the course's `GroceryStoreDataset/` folder with `classes.csv`, `train.txt`, `test.txt`, `val.txt`, and the referenced images. The VGG16 section expects `birds/` and `dogs/` image folders and downloads pretrained weights. Place these folders inside `HW1/`. |
| **HW2** | `trainEmotions.csv` and `testEmotions.csv`, alongside the notebook. | No additional dataset files are needed. |
| **HW3** | Notebook, saved output images, and report. | Place the CelebA dataset under `HW3/data/celeba/` in the layout expected by `torchvision.datasets.CelebA`. The notebook uses `download=False`. Training writes checkpoints into `HW3/`; later cells load `Generator_model_epoch_11.pkl`, `Generator_model_epoch_12.pkl`, and `Discriminator_model_epoch_12.pkl`. These checkpoints are not included. |

External course datasets and pretrained checkpoints are not bundled here. Use the original course materials for the HW1 image inputs. HW3 checkpoint filenames use zero-based epoch numbers; run at least 13 training epochs to create the files used by the visualization cells, or update those filenames to checkpoints from your own run.

## Repository layout

```text
HW1/
  neural-networks-and-computer-vision.ipynb
  report.pdf
HW2/
  text-emotion-classification.ipynb
  report.pdf
  trainEmotions.csv
  testEmotions.csv
HW3/
  face-generation-gan.ipynb
  report.pdf
  requirements.txt
requirements.txt
```

The root `requirements.txt` covers all three assignments. The file in `HW3/` points to the same dependency list. Downloaded datasets, local environments, and generated model weights are excluded from version control.

## Results and reproducibility

The notebooks retain their original experiment outputs and discussions, including classification curves and confusion matrices in HW2 and generated faces in HW3. These are recorded coursework results, not results from a fresh run in the environment above. Exact training outcomes depend on random seeds, hardware, and package versions.

The assignments were completed in pairs. Original submission details and assignment text remain in the notebooks and reports.
