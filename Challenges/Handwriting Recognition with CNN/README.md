# MNIST Digit Classification — Dense NN vs CNN

## 1. Project Overview  
This project compares two neural‑network architectures on the **MNIST** hand‑written digit dataset:

1. **Deep Dense Network (MLP)**  
   * Three hidden layers (256 → 128 → 64 neurons)  
   * Batch Normalisation + Dropout  
   * Adam optimiser, learning‑rate = 2 × 10⁻⁴  
   * Early Stopping (patience = 5)  
   * **Best validation accuracy ≈ 0.98**

2. **Convolutional Neural Network**  
   * Two Conv‑ReLU‑MaxPool stacks (32 & 64 filters)  
   * Dropout before final Dense layer  
   * Standard Adam optimiser  
   * Early Stopping (patience = 5)  
   * **Best validation accuracy ≈ 0.994**

The CNN attains higher accuracy with far fewer trainable parameters (≈ 35 k vs 245 k) but requires ~5‑6 × longer per epoch due to convolution operations.

---

## 2. Technologies Used  

| Purpose | Library / Framework |
|---------|--------------------|
| Data | `numpy`, `pandas`, `matplotlib` |
| Dataset loader | `tensorflow.keras.datasets.mnist` |
| Model building | **TensorFlow / Keras** (`Sequential`, `Dense`, `Conv2D`, `MaxPooling2D`, `BatchNormalization`, `Dropout`) |
| Callbacks | `EarlyStopping`, `Model.save_weights` |

---

## 3. How to Run  

1. Clone the repository and install the packages listed in `requirements.txt` (TensorFlow ≥ 2.9, NumPy, pandas, matplotlib).  
2. Launch `mnist_dense_vs_cnn.ipynb` in Jupyter / Lab **or** run `python train_models.py` from the project root.  
3. All data is downloaded automatically via `mnist.load_data()`.  
4. After training, weights are saved as `mnist_nn.weights.h5` (dense) and `mnist_cnn.weights.h5` (CNN).

---

## 4. Challenges Faced  

* **Confidence vs Loss spikes** – the dense model’s validation loss occasionally spiked despite smooth accuracy, indicating correct but low‑confidence predictions (high cross‑entropy).  
* **Over‑fitting in dense model** – mitigated with BatchNorm, heavy Dropout (0.5 / 0.4 / 0.3), and a modest learning rate.  
* **Long CNN training time** – per‑epoch runtime grew from ~10 s (dense) to ~80 s (CNN) despite fewer parameters, due to the sliding‑filter computations.  
* **Parameter interpretation** – visual‑inspection of misclassified digits showed ambiguous, stylised handwriting (e.g., 5 vs 6, 8 vs 9), underlining limits of fully‑connected features.

---

## 5. Future Improvements  

* **Batch‑size sweep** — test larger batches on GPU to shorten CNN epochs without hurting generalisation.  
* **Model checkpointing** — save the best CNN weights automatically when validation accuracy improves.  

