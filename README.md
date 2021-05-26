# EGA Data submission

Describe steps of data submission to EGA database (it is a pain for a first time submitter), data encryption and submission codes adapted from [Dr Salpie Nowinski](https://github.com/salpie)

## Apply EGA submission account

I wrote an email for the account request from EGA helpdesk, helpdesk@ega-archive.org. There maybe other approaches. Currently we need two files to obtain the account:

+ Data Processing Agreement (DPA), signed by the PI and institution, https://ega-archive.org/files/EGA_Data_Processing_Agreement_v1.0.pdf
+ Submittor's info, signed by the PI also, https://ega-archive.org/files/Authorised_submitters_list.docx

## Encrypting BAM files

This step can be processed prior to the account application as it may takes quite long time.

```
#!/bin/sh
#$ -cwd           # Set the working directory for the job to the current directory
#$ -j y

##----------------------Modification part---------------------
#$ -pe smp 4    # Request 4 core
#$ -l h_vmem=20G
#$ -N encrypt
#$ -l h_rt=20:00:00 # Request 40 hour runtime
#$ -t 1-3

module load java

samples=/data/BCI-EvoCa2/qingli/Projects/HighDepth_IBDs/C277/encrypted_data/samples.list
sample=$(sed -n "${SGE_TASK_ID}p" $samples)

java -Xmx70G -jar /data/BCI-EvoCa2/salpie/EGA/EgaCryptor/EgaCryptor.jar -file /data/BCI-IBD/NOVA/test/pipeline/data/C277/wgs/bwa_alignment/validated/$sample
```

## Sending encrypted files to EGA box

## Filling up metadata for the study
+ First of all, DO NOT USE Safri!!! Use other browser instead;
+ For the contact of DAC, do not add space between the telephone number;
## Notify EGA team Re submission completion

## Obtainning EGA acession number
