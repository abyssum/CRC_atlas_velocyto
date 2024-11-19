# CRC atlas - velocyto nextflow pipeline

#TODO: documentation
### 1.1. Usage

Example for 10X data

```
$ nextflow run main.nf --input_csv <sampleSheet.csv> --gtf_file <ref_anno.gtf> --masked_repeats <rmsk.gtf> --out_dir <~/outdir/> --platform 10X -profile cluster,conda
```

Example for 10X data

```
$ nextflow run main.nf --input_csv <sampleSheet.csv> --gtf_file <ref_anno.gtf> --masked_repeats <rmsk.gtf> --out_dir <~/outdir/> --platform BD -profile cluster,conda
```

**\<Arguments\>**

--input_csv           = path to the input CSV file (see below for details)

--gtf_file            = path to GTF file (used for the creation of the BAM files)

--masked_repeats      = path to the masked repeats file

--out_dir             = path to the output directory

--publish_dir_mode    = mode of publishDir directive (default: "copy")

--platform            = [str: 10X/BD] choose the platform the samples were sequenced on (default: "")

--convert_loom        = [str: true/false] renames the barcodes in the loom file according to the <cohort-sampleID-barcode> convention - this module is tested **only** on ICBI's CRC atlas datasets (default: "false")

--custom_loom_dir     = if `--confert_loom true` specify the ouput dir for the converted loom files


**Notes**

**Outpur directory

The pipeline will output the results in the /path/to/Sample.bam directory by default. You need to specify a directory through --out_dir otherwise.

**CSV file (default settings)**
```
study,sample_id,bam,bcl
cohort_1,sample_1,/path/to/Sample1_possorted.bam,/path/to/Sample1_barcodes.tsv
cohort_2,sample_2,/path/to/Sample2_possorted.bam,/path/to/Sample2_barcodes.tsv

```

* If you choose the `--platform 10X` you need to change the input CSV file to specify the cellranger directories instead of specific bam files (not tested yet)

**CSV file (run_10x flag)**
```
study,sample_id,bam
cohort_1,sample_1,/path/to/Sample1/
cohort_2,sample_2,/path/to/Sample2/

```