## Detecting Viral vs Bacterial Pneumonia from CXR with Deep Learning

### Items in Repository:

- README.md - a summary of the repository content
- Models_and_Results.ipynb - notebook with models and their performance
- /Step01_Data_Cleaning- codes for transfering images into the correct folder
- /Step02_Training- codes for models (Baseline dense, CNN, DenseNet121) 
- [/presentation](https://github.com/viviandng/flatiron-project-4/blob/master/Presentation/Pneumonia%20X-Ray%20Detection.pdf) - pdf file of the final presentation

### Prompt:

According to the [American Thoracic Society](https://www.thoracic.org/patients/patient-resources/resources/top-pneumonia-facts.pdf), Pneumonia is the world’s leading cause of death among children under 5 years of age, killing approximately 2,400 children a day. Pnemonia is also the number 1 most common reason for children to be hospitalized in the US. The managment of this disease costs the US over $13B every year. Although there are adequate treatment (oral and IV antibiotics, IV fluids, oxygen and rehydration therapy), the cause of pneumonia must be identified and treated promptly to prevent the misuse or lack of antibiotics that will cause long term complications and death. </br>

The goal of this project is to train and build a deep learning model that can classify whether a given patient has viral or bacterial pneumonia, given a chest x-ray image. This model will allow us to diagose the patient correctly and provide a proper course of treatment whether it is with or without antibiotics.

### Results:

| Model          | Accuracy | Precision |  F1   | **Recall** | Loss  |
| -------------- | :------: | :-------: | :---: | :--------: | ----- |
| Baseline Dense |  0.725   |   0.720   | 0.800 |    .900    | 0.580 |
| CNN            |  0.449   |   0.492   | 0.460 |   0.433    | 2.154 |
| DenseNet121    |  0.458   |   0.458   | 0.458 |   0.458    | 1.174 |

### Dataset

https://data.mendeley.com/datasets/rscbjbr9sj/2

- Train folder:
  - 2,404 BACTERIAL
  - 1,232 VIRAL
- Val folder:
  - 134 BACTERIAL
  - 113 VIRAL
- Test folder:
  - 242 BACTERIAL
  - 148 VIRAL

### Methodology:

1.	Use os to properly store images:
   - Download the dataset and extract only pneumonia chest x-ray images 
   - Transfer images to proper folders (bacterial vs viral folders for both train and test folders)
   - Create a validation folder by taking the first 134 bacterial images and 113 viral images from train folder
2.	Reshape images:
   - Resize = 224x224 
   - Rescale = 1./255
3.	Train models:
   - Create a baseline model with dense layers (fully connected)
   - Create a CNN model
   - Create a model with transfer learning (DenseNet121)
4.	Evaluate models by comparing accuracy, F1, precision, recall, loss scores
5.	Test the data on the best model (highest F1 score)

### Recommendations:

- Incorporate model to IT softwares (ex: epic) in hospital settings to assist health professionals diagnose the cause of pneumonia so patients can receive the proper treatment plan
- To enhance patient outcomes, use model under the supervision of a primary care physician 

### Next Steps:

- Improve the current model with additional chest x-ray data from adult patients 
- Train model with other transfer learning models (ex: ResNet)
- Explore machine learning solutions that detects whether a patient has heart failure or pneumonia, given chest x-ray
