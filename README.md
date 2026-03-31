# PU_Bagging
## Requirements  
Before run the program, please ensure that the following packages are installed:   
- PyTorch
- pymatgen
- scikit-learn  

## Overview

This project implements a Positive–Unlabeled (PU) Bagging learning framework for accurate classification tasks.  
The framework employs an ensemble strategy, where multiple base learners are trained on bootstrapped datasets.  

In this implementation, Crystal Graph Convolutional Neural Network (CGCNN) is used as the base model.  
The program is for PU Bagging learning, which trains an ensemble model to realise accurate classification.    

## Training the Base Model
You can train the initial CGCNN model using:  

`python main.py $train_data_dir --task classification --epochs 40 --wd 0.0005 --lr 0.001 --momentum 0.95 --atom-fea-len 64 --n-conv 3 --n-h 1 --h-fea-len 128`  

  ## PU Bagging Training  
  PU Bagging training is performed using:  
  
  `bash PU.sh`  
  
  This script trains an ensemble of models based on different resampled datasets.  

  ## Transfer Learning

After training the initial PU Bagging model, transfer learning can be applied to further improve performance:  

`python transform.py train_data_dir --model_path origin_model_path --task classification --epochs 45 --wd 0.0005 --lr 0.002 --momentum 0.95 --atom-fea-len 64 --n-conv 3 --n-h 1 --h-fea-len 128 --lr-milestones 30`

To complete the full pipeline (PU Bagging + transfer learning), run:  

`bash transfer_pu.sh`

## Prediction

Once the model is trained, you can predict the synthesizability probability using:  

`bash Test.pbs`

## Notes
`PU.sh`, `transfer_pu.sh`, and `Test.pbs` are PBS job submission scripts. If you are using other job scheduling systems (e.g., Slurm), these scripts should be modified accordingly.


