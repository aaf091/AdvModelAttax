# Adversarial Attack Benchmark on ImageNet Subset

This repository implements and evaluates several adversarial attack methods on a 100-class subset of ImageNet, focusing on patch-based and standard L∞  attacks against ResNet-34 and transferability to DenseNet-121.

---

## 📚 Project Structure

- **`Final.ipynb`**  
  Implements various adversarial attacks:
  - FGSM (Fast Gradient Sign Method)
  - PGD (Projected Gradient Descent)
  - Multipatch PGD
  - Targeted Patch PGD (fixed and subset targets)
  - Supercharged multi-patch variants (C1, C2)
  - Data loading utilities for a 100-class subset of ImageNet:
  - Mapping global labels (401–500) to WNIDs
  - Custom `SubsetDataset` and `FilteredImageFolder`
   - Evaluation scripts for computing Top-1 and Top-5 accuracy on adversarial sets and transfer to DenseNet-121.

- **`adv_test_set*.pt`**  
  Saved adversarial test sets (500 images each) for each attack variant.


---

## 🚀 Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/AdvModelAttax.git
   cd AdvModelAttax
   ```

2. Open Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

3. Download the 100-class ImageNet subset under `TestDataSet1/` and ensure `labels_list.json` is present.

4. Run the Jupyter Notebook with suitable CUDA GPU (Nvidia V100 or A100)

5. **Visualize samples**  
   Within notebooks or scripts, use provided visualization functions to compare original vs. adversarial images.

---

## 📊 Results Summary

| Attack Variant                                  | ResNet-34 Top-1 | ResNet-34 Top-5 | DenseNet-121 Top-1 | DenseNet-121 Top-5 |
|-------------------------------------------------|-----------------|-----------------|--------------------|--------------------|
| **Baseline (clean)**                            | 76.00%          | 94.20%          | 74.60%             | 93.60%             |
| **FGSM (ε=0.02)**                               | 6.00%           | 35.60%          | 63.60%             | 89.40%             |
| **PGD (ε=0.02)**                                | 0.00%           | 11.60%          | 64.00%             | 91.20%             |
| **Multipatch (6 patches)**                      | 19.40%          | 45.00%          | 63.00%             | 84.60%             |
| **Targeted Patch (single random target)**       | 73.80%          | 94.60%          | 74.00%             | 93.00%             |
| **Patch PGD (6 patches)**                      | 45.20%          | 80.20%          | 71.80%             | 92.60%             |
| **Multi Patches, Fixed Target**                 | 33.60%          | 67.20%          | 70.60%             | 90.40%             |
| **Multi Patches, Target Subset [401–500]**      | 35.00%          | 68.80%          | 69.60%             | 90.40%             |
| **Supercharged C1 (single target)**             | 1.80%           | 19.60%          | 56.80%             | 80.20%             |
| **Supercharged C2 (subset [401–500])**          | 1.00%           | 4.80%           | 54.80%             | 78.60%             |

*Note: Supercharged variants achieve Top-1 < 2% on ResNet-34.*

---

## ✍️ References

- Goodfellow et al., “Explaining and Harnessing Adversarial Examples” (FGSM)
- Madry et al., “Towards Deep Learning Models Resistant to Adversarial Attacks” (PGD)
- ChatGPT

## Authors
- Aadit Fadia
- Isha Math
- Riya Shah

---

## 🔗 License

MIT © Your Name
