# PU_Bagging

The program is for PU Bagging learning, which trains an ensemble model to realise accurate classification.  
Here, we use CGCNN as basic model. You can get your own model with:  

`python main.py $train_data_dir --task classification --epochs 40  --wd 0.0005 --lr 0.001  --momentum 0.95 -b 98 --atom-fea-len 64  --n-conv 3  --n-h 1 --h-fea-len 128`  

And PU Bagging learning is performed by `PU.sh`. The file is a submit script in PBS system. It should be adjusted in other job management system.  

After the training for the first PU Bagging model, transfer learning will be performed. The process can be finished by `transfer_pu.sh`.  

When you get the ideal model, you can use `Test.pbs` to predict the possibility of being synthesis.  




