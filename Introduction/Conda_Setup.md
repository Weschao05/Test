#Installing Miniconda3
1. Login in to Kepler and make sure you are in home directory
2. Install Miniconda3 and you should be in (base) at the end
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-py39_4.12.0-Linux-x86_64.sh
bash Miniconda3-py39_4.12.0-Linux-x86_64.sh

source .bashrc

conda ––version
```
3. Use the code “conda config --show channels” and you should see “default”. Please installed bioconda and conda forge and then check afterward if installation is complete
```bash
conda config --add channels bioconda
conda config --add channels conda-forge
```
4. Set up the following Conda Environments
```bash
#Trimming
conda create -n trimming -c bioconda -c conda-forge trim-galore fastqc
#Alignment
conda create -n alignment -c bioconda -c conda-forge hisat2 samtools
#Htseq
conda create -n counting -c bioconda -c conda-forge htseq
```
5. Activate your conda environments
```bash
conda activate <your_environment>
```
6. Optionally, you can set up aliases make faster access to your environment using your .bash_profile

