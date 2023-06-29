## DrugBAN Reusability

## Reproducing Our Results
To replicate our experimental results, please follow the steps below, adhering to the conventions typically used in the README files of scientific research papers on GitHub.

## Environment Setup
Begin by creating the necessary Anaconda environment. Refer to the original documentation provided at (https://github.com/peizhenbai/DrugBAN) for detailed instructions.

## Data Preparation
1. Locate the desired dataset within the **datasets** folder. For example, if you wish to reproduce the results from the resplit experiment, access the **datasets/resplit** folder.
2. Copy the contents of the selected **datasets** folder (including subfolders and files) to the corresponding location in the **DrugBAN/datasets** directory.
3. Repeat this process for any additional datasets required for your replication.
You are now ready to proceed with reproducing the experimental results.

## Reproducing the Results
To reproduce our experimental results, you should first create the necessary Anaconda environment based on the original documentation provided at (https://github.com/peizhenbai/DrugBAN). The **datasets** folder contains the data used in DrugBAN, including resplit, r-cluster, and k-cluster. In the **datasets/resplit** folder, we have full data with both random and clustering-based splits for both the in-domain and cross-domain experiments. Furthermore, in the **datasets/r-cluster** and **datasets/k-cluster** folders, we have the complete data with two clustering-based splits for the cross-domain experiment.

### Reproducing the Results of the re-split Experiment
To utilize the re-split dataset we created, you can proceed with the experiments using the following parameters:

For the in-domain experiments with vanilla DrugBAN, run the following command, replacing ${dataset} with either bindingdb, biosnap, or human:
```
python main.py --cfg "configs/DrugBAN.yaml" --data resplit/${dataset} --split random
```

For the cross-domain experiments with vanilla DrugBAN, run the following command, replacing ${dataset} with either bindingdb or biosnap:
```
python main.py --cfg "configs/DrugBAN_Non_DA.yaml" --data resplit/${dataset} --split cluster
```

For the cross-domain experiments with CDAN DrugBAN, run the following command, replacing ${dataset} with either bindingdb or biosnap:
```
python main.py --cfg "configs/DrugBAN_DA.yaml" --data resplit/${dataset} --split cluster
```

### Reproducing the Results of the r-cluster Experiment
To utilize the dataset obtained from single-linkage clustering, you can proceed with the cross-domain experiment using the following parameters:

For the cross-domain experiments with vanilla DrugBAN, run the following command, replacing ${dataset} with either bindingdb or biosnap:
```
python main.py --cfg "configs/DrugBAN_Non_DA.yaml" --data r-cluster/${dataset} --split cluster
```

For the cross-domain experiments with CDAN DrugBAN, run the following command, replacing ${dataset} with either bindingdb or biosnap:
```
python main.py --cfg "configs/DrugBAN_DA.yaml" --data r-cluster/${dataset} --split cluster
```

### Reproducing the Results of the k-cluster Experiment
To utilize the dataset obtained from single-linkage clustering, you can proceed with the cross-domain experiment using the following parameters:

For the cross-domain experiments with vanilla DrugBAN, run the following command, replacing ${dataset} with either bindingdb or biosnap:
```
python main.py --cfg "configs/DrugBAN_Non_DA.yaml" --data k-cluster/${dataset} --split cluster
```

For the cross-domain experiments with CDAN DrugBAN, run the following command, replacing ${dataset} with either bindingdb or biosnap:
```
python main.py --cfg "configs/DrugBAN_DA.yaml" --data k-cluster/${dataset} --split cluster
```

Additional Information:
If you are using a Linux system, it's possible that some library versions in the Anaconda environment you create may differ from those specified in the original documentation. This can vary depending on your hardware configuration. The r-cluster folder contains the results obtained from single-linkage clustering, while the k-cluster folder contains the results obtained from k-means clustering. After clustering, we performed random data splits using five different random seeds, following the proportions mentioned in the original paper. In this case, we have provided the results of only one random data split. Please ensure that you take into account the potential library version discrepancies and adjust them accordingly in your environment to ensure compatibility and effectively reproduce the results.

## Incorporating an Early Stopping Strategy into the Experiment
If you want to incorporate an early stopping strategy during the model training, you can replace the **train.py** file in the **DrugBAN** folder with the modified **train.py** file. This updated **train.py** file should contain the necessary code for implementing early stopping in the training process. By using this modified file, you can enable early stopping functionality in your model training.

## Changing the Pooling Strategy to Max Pooling
To change the model's pooling method to max pooling, you can replace the **ban.py** file in the **DrugBAN** folder with the modified **ban.py** file. This updated **ban.py** file should contain the necessary code for implementing max pooling as the pooling mechanism in the model. By using this updated file, you can switch the pooling method to max pooling in your model.

## Drug Response Prediction Using DrugBAN with/without CDAN module
To employ the DrugBAN in drug response prediction, you can replace the **models.py** file and **dataloder.py** file in the DrugBAN folder with the modified **models.py** file and **dataloder.py** file.
To reproduce the results of cancer cell and drug response prediction, please follow the instructions below and use the provided parameters for experimentation:

For the cross-domain experiments with vanilla DrugBAN, run the following command:
```
python main.py --cfg "configs/DrugBAN_Non_DA.yaml" --data drug_cell --split cluster
```

For the cross-domain experiments with CDAN DrugBAN, run the following command:
```
python main.py --cfg "configs/DrugBAN_DA.yaml" --data drug_cell --split cluster
```


