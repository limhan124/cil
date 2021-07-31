# CIL_PROJECT

## 1. Setting

You can use winSCP to upload datasets to leonhard cluster.

1. Log in the Leonhard cluster

2. Clone the github repository and change the directory to the repository: 
```
git clone link_for_repository.git
```

```
cd CIL_PROJECT
```

*If the CIL_PROJECT has been updated, you need to clone the repository again. You can remove the old one with 'rm -rf CIL_PROJECT'. Or you can use winSCP to update and modify the codes in a more convenient way.*

3. Set up the virtual environment and modules
```
source init_leonhard.sh
```
*You need to create a virtual environment first by running 'python -m venv venv'. Afterwards, a virtual environment called venv is created in your home directory*

4. Submit the jobs, parameters specify the number of the gpus and the memory we request, and the time limit we set for our task
```
bsub -oo nexist/haha.out -R "rusage[ngpus_excl_p=1,mem=20000]" -W 24:00 python baseline1.py 
```

*The -oo command with a nonexistent folder trick will make the leonhard send you an email once the job is finished

*Don't use a root directory for the submitted file such as ~/CIL_PROJECT/data_load.py, this will cause the 'permission denied' error. Use an absolute path when you need to read some files such as /cluster/home/jiduwu/CIL_PROJECT*

5. 'bjobs' - command to see if the job is running or pending; 'bpeek job_id' - command to monitor the job; 'vim lsf.oJobID' - command to read the output file for the job; If you use winSCP, you can observe and read the file directly.

## 2. Our repository is divided into three modules: CRF-postprocessing, Additional data and data preprocessing, and Model

To replicate our results, you need the following steps

1. Add the extra data in *Additional data and data preprocessing*, make sure they are in the correct corresponding directory.

2. All the results can be obtained by run the (similar) command in step 4 above. :)

3. For higher time efficiency, some of our results are obtained by loading models we trained before, and the best model can be accessed through this link https://drive.google.com/file/d/1rVrhZfrLUrZ7JxdU3mEfTUFC2A-4nhaJ/view?usp=sharing.


