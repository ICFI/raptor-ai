# raptor-ai

## Data preparation steps

Step 1. Download data from the Google archive that hosts the wiki-links data. [Link](https://code.google.com/archive/p/wiki-links/downloads) to data.

Step 2. Deploy the ETL job that is intended to prepare the data.

  a.	Details on the ETL job:  The ETL job preps the Google wiki-links data from a normalized format to a flattened out deformalized format as shown below.

  Snapshot of google Wiki-links data
  
  ![alt text](https://github.com/ICFI/raptor-ai/blob/master/wikilinks_data_snapshot.PNG "Logo Title Text 1")


Snapshot of data after transformation

"1001","ftp: //212.18.29.48/ftp/pub/allnet/nas/all60300/ALL60300_UM_V12_EN.pdf r NetBIOS acting whose capabilities ME calls preferably functionality anything boost enjoying"

b.	Find below the data prep job snapshot.  The job is built on an open source ETL tool – Talend 6.x.  For more info please visit the Talend Data Integration page 

  ![alt text](https://github.com/ICFI/raptor-ai/blob/master/data_prep_job_snapshot.png "Logo Title Text 1")
  
c.	Deploying the job for execution: 
*	Pre-requisites: Windows 7 and above, Java JRE 8.x, enough space to house the raw data files and cleansed files.
*	Unzip the contents of data_prep_job1_1.1.zip file to a local folder.   
*	To run the job execute the data_prep_job1_run.bat file.  The job will prompt for the location of the input file.  The output will reside in C:\Temp\USCIS_RFI in a csv format.


## Classification environment setup

The classification prototype utilizes a GPU environment that is based on the NVDIA DIGITS platform.  A GPU based architecture/platform is ideal for running deep learning algorithms.  

Step 1. To setup, a GPU environment AWS and Azure provides GPU specific instances.  Recommended AMIs on the AWS platform - g3.4xlarge or p2.xlarge.  

Step 2. Install the NVIDIA DIGITS platform along with supporting packages on Ubuntu 16.04

a.	The setup includes -  CUDA, CUDnn, DIGITS, Caffe and Torch.  Please follow the instructions at: [DIGITS Install](https://github.com/NVIDIA/DIGITS/blob/master/docs/UbuntuInstall.md).

b.	Open a browser session and check if the DIGITS interface is available.  http://<ipAddress> 

## Data setup steps
Step 1. Import the outputs from the data preparation into the GPU instance

Step 2. Partition the data set into 70/20/10

Step 3. Open the DIGITS interface to setup a job that will perform the training and validation of data.

![alt text](https://github.com/ICFI/raptor-ai/blob/master/DIGITS_data_prep.PNG "Logo Title Text 1")

The training/validation process should take about 10minutes using the DIGITS GPU environment.  If it takes more time, please check the settings to ensure that it is not using the CPUs to setup the data set.
