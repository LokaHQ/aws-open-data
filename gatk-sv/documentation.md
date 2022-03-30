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
