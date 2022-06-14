# Cassava-Leaf-Disease-Classification
We have developed different CNNs to classify the images from [Cassava Leaf Disease](https://www.kaggle.com/competitions/cassava-leaf-disease-classification/overview) repositoy in kaggle. We used pretrained CNNs (InceptionResNetV2 and EfficientNetB3) applying tasks of transfer learning and fine-tuning. We have also developed our own custom CNN. For both processes we applied regularization techniques and data augmentation

The dataset is formed of images from 5 different classes. In the images we can find plants with different colours and textures due to their health. The goal of this project is to study the chance to create a model capable of classify the images and their health/disease.

the dataset is divided in:

| Label | Total of images |
|:------|:----------------|
| Cassava Mosaic Disease (CMD) |    13158 |
| Healthy |    2577 |
| Cassava Green Mottle (CGM) |    2386 |
| Cassava Brown Streak Disease (CBSD) |     2189 |
| Cassava Bacterial Blight (CBB) |    1087 |

## Final result

At the end we have found that our custom CNN is more accurate than the pre-trained ones.

### Custom CNN

| precision | recall | f1-score |  support |
|:-----|:-----|:---------|:-----|
|     Cassava Bacterial Blight (CBB)   |    0.00   |   0.00  |    0.00    |   358|
|Cassava Brown Streak Disease (CBSD)   |    0.13   |   0.03 |     0.05 | 547|
|         Cassava Green Mottle (CGM)   |    0.13   |   0.03   |   0.04   |    596|
|       Cassava Mosaic Disease (CMD)   |    0.61    |  0.90   |   0.73   |   3290|
|                            Healthy   |    0.15   |   0.08  |    0.10   |    645|
|                                      |             |       |           |         |
|                           accuracy   |           |          |   0.56    |  5436|
|                          macro avg   |    0.20   |   0.21   |   0.18    |  5436|
|                       weighted avg   |    0.41   |   0.56   |   0.46    |  5436|


### InceptionResNetV2

| precision  |  recall  | f1-score  | support|
|:-----|:-----|:---------|:-----|
|     Cassava Bacterial Blight (CBB)   |    0.03   |   0.01   |   0.02    |   217|
|Cassava Brown Streak Disease (CBSD)   |    0.11   |   0.16   |   0.13    |   438|
|         Cassava Green Mottle (CGM)   |    0.10   |   0.04   |   0.05    |   477|
|       Cassava Mosaic Disease (CMD)   |    0.62   |   0.59   |   0.60    |  2632|
|                            Healthy   |    0.12   |   0.19   |   0.15    |   516|
|                                      |           |           |         |         |
|                           accuracy   |           |           |  0.41    |  4280|
|                          macro avg   |    0.19   |   0.20    |  0.19    |  4280|
|                       weighted avg   |    0.42   |   0.41    |  0.41    |  4280|
                      
### Summary 

The next table sums up the evolution of the custom model with different parameters

| Índice | Batch size | Dropout | Weight and bias regularization | First Dense | Dense number | accuracy-val_accuracy |
|:-----|:-----|:---------|:-----|:---------|:-----|:-----|
| 1 | 16 | 0.25 | NO | 256 | 3+1 | 0.87-0.64 |
| 2 | 16 | 0.7 | YES | 256 | 3+1 | 0.64-0.66 |
| 3 | 16 | 0.5 | NO | 256 | 3+1 | 0.83-0.72 |
| 4 | 16 | 0.25 | NO | 64 | 2+1 | 0.83-0.67 |
| 5 | 8 | 0.25 | YES | 128 | 2+1 | 0.72-0.71 |
| 6 | 4 | 0.25 | YES | 64 | 2+1 | 0.62-0.67 |
| 7 | 8 | 0.25 | YES | 64 | 2+1 | 0.69-0.75 |

This tables compares the accurracy between the two pre-trained models used.

| Arquitectura | Accurracy |
|:-----|:-----|
| InceptionResNetV2 with Transfer Learning | 0.37 | 
| EfficientNetB3 with Transfer Learning | 0.35 |
| InceptionResNetV2 with Fine Tuning | 0.41 |
| EfficientNetB3 with Fine Tuning | 0.37 |

## Conclusion

As you can see the custom model has better accurracy but that doesn't mean that is a good model. Although, it is a bad model because is overfitted and it can only predict one class from the five. This is because in the dataset used the >60% of the images are from the CMD class and even with data augmentation and other techniqques we found it impossible to create an accurate model witout overfitting. 
