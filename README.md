# Bias-Mitigation

Code and data for the article **"Mitigating Algorithmic Bias in Multiclass CNN Classifications Using Polynomial Causal Modeling"** (Amebley and Owusu-Agyemang, submitted to *Discover Computing*).

## Contents

| File | Description |
|---|---|
| `Data_Preparation_file.ipynb` | Python (Google Colab). Loads FairFace, generates emotion labels with DeepFace, splits the data, trains the CNN (Section 3.2, Table 3) and produces predictions for the test set. |
| `Polynomial_Causal_Modeling.ipynb` | R. Bias detection, linear causal baseline, polynomial causal model and Equalized Odds baseline (Sections 3.3–3.5, Section 4). Reads `multiclass_data.csv`. |
| `multiclass_data.csv` | The original prediction file on which **all results in the article are based**: 5,477 test images, with DeepFace emotion scores, the CNN's predicted class probabilities, gender, age and race. |
| `train_labels.csv and val_labels.csv` | DeepFace emotion labels for all 97,698 images (training, validation, test). **Regenerated** with the same pre-trained model and code, because the original label files were not retained. |

## Data sources

- **FairFace** (Kärkkäinen and Joo, 2021): https://github.com/joojs/fairface (CC BY 4.0). The training (86,744) and validation (10,954) partitions were used. The images are not redistributed here.
- **DeepFace** (Serengil and Ozpinar): https://github.com/serengil/deepface, version [0.0.93], default face detector, detection non-enforced.

## Reproducing the analysis

1. To reproduce the article's results, run `Polynomial_Causal_Modeling.ipynb` on `multiclass_data.csv` (an R kernel is needed).
2. To rerun the CNN pipeline, download FairFace, edit the paths in `Data_Preparation_file.ipynb`, and run it in order. Retraining produces a new model whose predictions will differ slightly from `multiclass_data.csv`; the article's results come from the original file.

## Notes

- **Age labels.** In `multiclass_data.csv`, the FairFace age brackets "10–19" and "3–9" appear as "19-Oct" and "9-Mar", because spreadsheet software converted them to dates. The R notebook converts them to 19 and 9 (upper bounds); all other brackets are coded as midpoints, and "more than 70" as 75.
- **Software versions:** Python [3.13.16], TensorFlow/Keras [2.12.0], DeepFace [0.0.93]; R [4.6.1].

## Licence

CC BY 4.0 (see `LICENSE`). Please cite the article and this repository.

## Contact

Kisseh Amebley, Kwame Nkrumah University of Science and Technology, kamebley1@st.knust.edu.gh
