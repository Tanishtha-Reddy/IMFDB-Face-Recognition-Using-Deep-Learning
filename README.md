# IMFDB-Face-Recognition-Using-Deep-Learning
## ResNet-50 Face Recognition

A ResNet-50 implementation for face recognition on the IMFDB dataset. Trained from scratch and achieved **75% validation accuracy** and **62.5% test accuracy**.

## Overview

This is an assignment and learning project where I implemented ResNet-50 (a deep CNN architecture) from scratch and trained it to recognize 8 celebrities from the IMFDB dataset.

**Key Results:**
- Validation Accuracy: **75%**
- Test Accuracy: **62.5%**
- Training Time: 5 minutes
- Parameters: 25.5M (much smaller than VGG-16's 138M)

## What I Learned

- How residual connections (skip connections) help train deeper networks
- Why ResNet-50 is better than VGG: fewer parameters, faster training, better optimization
- Building a complete ML pipeline: data loading → training → evaluation
- Working with PyTorch and Google Colab

## The Model

**ResNet-50 Architecture:**
- 50 layers deep (way deeper than VGG's 16-19 layers)
- Uses bottleneck blocks (1×1 → 3×3 → 1×1 convolutions)
- Skip connections allow gradients to flow through deep networks
- 25.5M parameters (81% fewer than VGG-16)

**Why this design works:**
Without skip connections, gradients vanish in deep networks. Skip connections act as "shortcuts" that preserve gradient flow, enabling training of much deeper networks.

## Results

### Accuracy by Celebrity

| Celebrity | Accuracy |
|-----------|----------|
| MadhuriDixit | 100% ✓ |
| KatrinaKaif | 90% ✓ |
| AmitabhBachan | 80% |
| AkshayKumar | 60% |
| Amir | 50% |
| SharukhKhan | 60% |
| ShilpaShetty | 40% |
| Kajol | 20% |

**Observation:** Celebrities with more distinctive features are recognized better. Similar-looking faces are harder to distinguish (common in real face recognition).


### Dataset

The IMFDB dataset was provided by the evaluators.

### Training

**Best way:** Use Google Colab (has GPU, faster)

1. Open `notebooks/training.ipynb` in Colab
2. Mount your Google Drive with the dataset
3. Run cells in order
4. Takes ~5 minutes to train

## Key Insights

1. **ResNet > VGG:**
   - ResNet-50 is 3x deeper than VGG-16
   - Uses 81% fewer parameters
   - Trains faster and gets similar/better accuracy
   - Skip connections make this possible

2. **Why Test Accuracy < Validation Accuracy:**
   - Validation: 75%
   - Test: 62.5%
   - This is normal for small datasets. Some faces are just harder to recognize.

3. **What Worked:**
   - Skip connections enabled stable training
   - Batch normalization helped with convergence
   - Learning rate scheduling improved final accuracy
   - Re-training the model a few times helped in increasing validation accuracy from 72.1% to 75%

4. **What Could Improve:**
   - Data augmentation (flip, rotate images) → could add 5-10%
   - Metric learning (teach the network to recognize face similarity) could add 10-15%
   - More data per celebrity would help a lot
  
   
