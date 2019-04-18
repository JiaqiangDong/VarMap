# VarMap

Please cite the pipeline with the following paper:
Dong, J. , Tu, M. , Feng, Y. , Zdepski, A. , Ge, F. , Kumar, D. , Slovin, J. P. and Messing, J. (2019), Candidate gene identification of existing or induced mutations with pipelines applicable to large genomes. Plant J, 97: 673-682. doi:10.1111/tpj.14153

1. Ask the administer of the cluster to register an account and create a working directory named analysis under the home directory. All the input and output files will be stored there. 

Type:mkdir analysis

Type:cd analysis

2. Download and unpack the software_package.tar.gz from the following link:
https://github.com/JiaqiangDong/VarMap/

Type:tar -xvzf software_package.tar.gz

Make sure the software_package folder is in the working directory named analysis under the home directory.

3. Move the scripts “VarMapDNA.sh” or “VarMapRNA.sh” and annotation.sh to the working directory.

Type:mv ./software_package/VarMap*NA.sh ./

Type:mv ./software_package/annotation.sh ./

4. Download the reference genome sequence file into the working directory according to the reference_link.txt file. For example, for maize, open the reference_link.txt file, copy and paste the line to download the genome.

Type:curl -O ftp://ftp.ensemblgenomes.org/pub/release-31/plants/fasta/zea_mays/dna/Zea_mays.AGPv3.dna.toplevel.fa.gz

Download the reference genome annotation file into the working directory according to the the species. For example, for maize, open the reference_link.txt file, copy and paste the line to download.

Type:curl -O ftp://ftp.ensemblgenomes.org/pub/release-31/plants/gff3/zea_mays/Zea_mays.AGPv3.31.gff3.gz

Type: gunzip *.gz
 
If the genome file isn’t in the list, please type in the link to the genome/annotation file after “curl -O” to download both the genome and annotation files.
 
5. Copy or move the paired end fastq files into the working directory. 

6. Open the VarMapDNA.sh or VarMapRNA.sh to change the parameters.

Type:vi VarMapDNA.sh
or
Type:vi VarMapRNA.sh

Type:i

Modify the header lines (beginning with #PBS) of the script file according to the cluster. (Different cluster have different header lines, ask the administer, please)

Only 6 parameters needs to be changed. One is the “path”, which is the path to the working directory where all the files are stored. The second one is the “REFS”, which is reference genome. The third and fourth ones are the “read1” and “read2”, which are the filenames of the paired end reads of mutant. The fifth and sixth ones are the “read3” and “read4”, which are the filenames of the paired end reads of wide type.

Change the email address to your own, so that the notification will be sent when the pipeline starts or ends.

7.Submit the VarMapDNA.sh or VarMapDNA.sh to run on the cluster. (Different cluster have different commands, ask the administer, please)

8.Run the annotation.sh script to annotate the mutant specific variants. 

Type:Chmod 744 annotation.sh

Type:./annotation.sh
