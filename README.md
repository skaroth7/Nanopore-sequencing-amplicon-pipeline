Create conda container
- conda create -n ONT_amplicon_pipeline

Activate conda environment
- conda activate ONT_amplicon_pipeline

Requirements:
Install requirements
- conda install bcftools
- conda install vcftools
- conda install porechop
- conda install minimap2
- conda install nanopolish
- conda install whatshap
- conda install snakemake

First run prepare_fastq_data.py ##this assumes you are using multiple barcode samples with the fastq files seperated into separate folders based on the barcode number (standard Minknow output)
- place the prepare_fastq_data.py file into the base directory containing all of the sequencing output folders
- cd to the base directory i.e.| cd "/WORKSPACE/Oscar/OG_15_04_24_PEGS6/20240415_1341_X4_ASU393_50637ee3/"
- python3 prepare_fastq_data.py "/sequenceout_directory/"                 ####note "/sequenceout_directory/" is a place holder, replace this with the data directory containing all of the seqecing output files

Modify the config.json to specify your required sequencing files and number of cores per sample. Additionally, you can run multiple samples using multiple threads by specifying the number of cores when running the snakefile with the instructions described below (INT = number of samples to run together).

Run the snakemake pipeline
- cd to the directory containing the snakefile
- i.e| cd "/WORKSPACE/snakemake_files/"
- snakemake --cores INT
