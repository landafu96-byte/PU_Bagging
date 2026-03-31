# PU_Bagging

Before run the program, please ensure `PyTorch`, `pymatgen` and `scikit-learn` are installed.  

The program is for PU Bagging learning, which trains an ensemble model to realise accurate classification.  
Here, we use CGCNN as basic model. You can get your own model with:  
`python main.py $train_data_dir --task classification --epochs 40  --wd 0.0005 --lr 0.001  --momentum 0.95 -b 98 --atom-fea-len 64  --n-conv 3  --n-h 1 --h-fea-len 128`  
And PU Bagging learning is performed by `PU.sh`. 

After the training for the first PU Bagging model, transfer learning will be performed by: 
`python transform.py train_data_dir --model_path origin_model_path --task classification --epochs 45  --wd 0.0005 --lr 0.002  --momentum 0.95 -b 164  \
 --atom-fea-len 64  --n-conv 3  --n-h 1 --h-fea-len 128 --lr-milestones 30`
The whole training process can be finished with `transfer_pu.sh`.  

When you get the ideal model, you can use `Test.pbs` to predict the possibility of being synthesis.  

(NB: `PU.sh`, `transfer_pu.sh` and `Test.pbs` are submit scripts in PBS system. They should be adjusted in other job management systems.)




