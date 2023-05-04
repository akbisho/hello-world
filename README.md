# hello-world
Creating this repository for my medical bioinformatics class! Super interesting stuff!
My name is Alex Bishop and I am a senior biochemistry major at Clemson University. Hopefully bioinformatics will transform the way we treat disease

Lab Overview:
In this lab, we will be using the SRA archive of triple negative breast cancer to create a Gene Expression Matrix (GEM) against normal breast tissue. Three years ago my grandmother was diagnosed with triple negative breast cancer. Thanks to her excellent medical team and her perseverance, she made short work of it. Triple negative breast cancer is the most aggressive and fastest metathesizing type breast cancer, therefore better understanding its composition can prove valuable for earlier recognition, and treatment.

Learning Objectives:

Learn how to install GEMmaker dependencies
Learn how to identify human SRA files from SRA archive
Learn how to create and normalize a GEM
Lab Tasks

Task A: Install GEMmaker

Install Nextflow - GEMmaker requires nextflow
#update software
sudo apt update
#Install java
sudo apt install default-jre

#compile nextflow
https://get.nextflow.io | bash

Install the GEMprep environment
conda create -n gemprep python=3.6 matplotlib mpi4py numpy pandas r scikit-learn seaborn
source activate gemprep

git clone https://github.com/SystemsGenetics/GEMprep

Task B: Download SRA files

Install normal subtype
wget https://trace.ncbi.nlm.nih.gov/Traces?run=SRR24377141

Install cancerous subtype
wget https://trace.ncbi.nlm.nih.gov/Traces?run=SRR23930149

Task C: Create and normalize the GEM

create the GEM
python ~/Desktop/classroom/myfiles/working_directory/GEMprep/bin/merge.py breast-rsem-fpkm.gtex.txt triplenegative-rsem-fpkm-tcga-t.txt breast-gtex-triplenegative.txt

normalize the GEM
python ~/Desktop/classroom/myfiles/working_directory/GEMprep/bin/normalize.py breast-gtex-triplenegative.txt breast-gtex-triplenegative.quantile.txt --quantile
