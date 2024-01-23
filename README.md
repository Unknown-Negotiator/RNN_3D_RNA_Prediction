# RNA bioinformatics - M2-GENIOMHE project

**[Project Presentation](https://docs.google.com/presentation/d/1hIQLwLdHiqBkKJV0TIPdSKCG0pdY6B-_Vd3H32T0SBA/edit?usp=sharing)**

## Repository

- `data`: a folder with the training (`data/TrainingSet`), testing (`data/TestSet`), sample (`data/sample`) folders and `SPOT-RNA-1D` folder.
  The `sample` folder contains a `.fasta` file that should be used to do inference for the delivery.
  The `SPOT-RNA-1D` folder contains the predictions from `SPOT-RNA-1D` for the Training set (`data/SPOT-RNA-1D/training.json`) and Test set (`data/SPOT-RNA-1D/test.json`). `angles` folder in `data` contains `.csv` files for each sequence with all angles for it's nucleotides.
- `rna_angles_prediction_dssr`: is a folder where a cloned code from this [repository](https://github.com/EvryRNA/rna_angles_prediction_dssr/tree/main). It computes angles for provided `TestSet` and `TrainingSet` in the data.
- `models`: folder where we store our pre-trained models
- `results`: folder where we store comparisons (MAE) of our model with prediction of SPOT-RNA-1D
- `src`: a folder where we implement our solution. Lets take a closer look at its components.

## src

- `__init__.py`: initialization of a package
- `main.py`: modify and run this code to check functionality of all modules within the package
- `data_extraction.py`: extract the needed angles provided by dssr
- `utils.py`: modify the data so that it become feedable to a model
- `visualisation.py`: functionality to view distribution of angles in provided datasets
- `models.py`: implementation of LSTM regressor and classifier for angle predictions
- `train.py`: functions which train the models
- `evaluate.py`: functions to test the accuracy of trained models
- `angles_helper.py`: used as an interface with the user to run the inference on provided .fasta file

## Example of CLI run

This package is designed to be executed through the CLI using Python. Below is an example demonstrating the usage of the package with detailed explanations for the required arguments.

`--input_path`: an absolute path to the input fasta file containing RNA sequences for inference.
Example of the fasta file contents:
" >17EP
ACGUUCU
"

`--out_path`: an absolute path to write the model output in JSON format.

`--model_type`: Specifies the model to be used for inference. Choose from the following options:

- `binary`: Binary model
- `tertiary`: Tertiary model
- `20`: 20-class quantized model
- `30`: 30-class quantized model
- `regression`: Regression model
- `gmm`: GMM inferred binary classifier

Example run, initiated from the `src` directory:

```bash
python3 angles_helper.py \
    --input_path '../data/sample/example.fasta' \
    --out_path '../results/test_output.json' \
    --model_type 'binary'
```

This example command initiates the `angles_helper` package, providing the necessary input parameters. Adjust the paths and model type based on your specific use case. The output will be stored in the specified JSON file.


## How to get started with the models

1. Navigate to rna_angles_prediction_dssr folder and run python dssr_wrapper.py

2. Navigate to the root/src folder and run main.py

3. Add modifications to main to test desirable functionality
