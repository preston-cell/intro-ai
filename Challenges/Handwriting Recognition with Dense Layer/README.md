# MNIST Hand‑Written Digit Classifier with Shallow MLP

## 1. Project Overview  
This project builds and tunes a **multilayer perceptron (MLP)** to classify the 28 × 28 grey‑scale images in the classic **MNIST** dataset (digits 0‑9).

Starting from a two‑layer baseline, we explored:

* Capacity changes (128 → 256 → 128 neurons)  
* Regularisation (Batch Normalisation, Dropout)  
* Learning‑rate / batch‑size tweaks  
* Early Stopping to halt training when validation loss stopped improving  

The final model reaches **≈ 95 – 97 % validation accuracy** with far less over‑fitting than the initial attempt.

---

## 2. Technologies Used  

| Purpose | Library / Framework |
|---------|--------------------|
| Data | `numpy`, `pandas` |
| Dataset loader | `tensorflow.keras.datasets.mnist` |
| Model building | **TensorFlow / Keras** (`Sequential`, `Dense`, `BatchNormalization`, `Dropout`) |
| Pre‑processing | **scikit‑learn** (`StandardScaler`, `train_test_split`) |
| Optimisation | `Adam` optimiser |
| Visualisation | `matplotlib` |

---

## 3. How to Run  

1. **Clone** the repository to your machine.  
2. Launch `mnist_mlp_classifier.ipynb` in Jupyter/Lab **or** run `train_mnist_mlp.py` with Python.  
   *The MNIST data downloads automatically on first run.*

---

## 4. Challenges Faced  

* **Early over‑fitting** – the baseline model hit 99 % train accuracy while validation loss climbed.  
* **Mis‑classified hard digits** – blurred or stylised 5/6/8/9 samples confused the network.  
* **Validation‑loss spikes** – mitigated by adding BatchNorm and higher Dropout rates.  
* **Training‑time trade‑offs** – lowering the learning rate required more epochs; compensated by using a slightly larger batch size.

---

## 5. Future Improvements  

* Apply simple **image augmentations** (small rotations, shifts) for greater robustness.  
* Test a **lightweight CNN** (Conv‑Pool‑Dense) for potentially higher accuracy with modest extra complexity.  

