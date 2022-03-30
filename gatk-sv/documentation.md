# GATK-SV Documentation

This repository holds the data needed to run the [GATK-SV pipeline](https://github.com/broadinstitute/gatk-sv) in AWS.

 
The data contained in this package contains, among others, the following data:
* Illumina short-read whole-genome CRAMs or BAMs, aligned to hg38 with [bwa-mem](https://github.com/lh3/bwa). BAMs must also be indexed.
* Indexed GVCFs produced by GATK HaplotypeCaller, or a jointly genotyped VCF.
* Family structure definitions file in [PED format](https://gatk.broadinstitute.org/hc/en-us/articles/360035531972-PED-Pedigree-format). Sex aneuploidies (detected in [EvidenceQC](#evidence-qc)) should be entered as sex = 0.
* Reference files from the human reference genome Hg38.

For more information please look at https://github.com/broadinstitute/gatk-sv.

## Bucket structure

The data can be found in the `s3://gatk-sv-data` bucket in the us-east-2 (Ohio) region.

```bash
gatk-sv-data
├── bams
├── cram
├── reference
│   ├── broad-ref
│   ├── gatk-sv-resources
│   ├── gvcf
│   └── batch_sv.test_large.qc_definitions.tsv
└── README.md
```

## Folder Details
Below are the details regarding the files and purpose of these folders.
| FiS3 Prefix inside s3://gatk-sv-datale | Description |
| :--- | :---------- |
| `bams/` | All the bams and bai index files needed for 156 - 1000 Genomes samples. If these are copied and used, the first step of cram-to-bam conversion will be skipped. This will save on time and cost of the overall pipeline. |
| `cram/` | All the cram and crai index files needed for 156 - 1000 Genomes samples. |
| `reference/broad-ref/` | The reference files needed for the pipeline consisting of GRCH38 assembly files, bed, ped and index files. These are static and could be used for other samples.|
| `bareference/gatk-sv-resources/` |This folder consists of reference tsv, txt, bed files needed for 1kg samples, gatk processes and framework related. These would need to be updated in case of running samples other than 1000 Genomes. |
| `reference/gvcf/` | All the Haplotype called g.vcf.gz and there index files needed for the 156 - 1000 Genome sample processing.|
| `reference/batch_sv.test_large.qc_definitions.tsv/` | This file is speicific to last module of the pipeline used for comparing the qc results. |
| `gcp_data_not_used/` | This file is speicific to last module of the pipeline used for comparing the qc results. |

These folders are also referenced in the [AWS setup scripts](https://github.com/goldfinchbio/aws-gatk-sv/blob/master/scripts/aws_setup_script.sh), so ensure these are in sync with the FSxL or S3 bucket being used for running the pipeline.


#
**We are working on coming up with concrete steps for identifying and updating the reference files on case basis. Please watch out for the updates here.** 