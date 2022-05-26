# iScanVCFMerge

iScanVCFMerge is a [Python](https://www.python.org) tool to facilitate the cross-species application of [Illumina iScan system](https://www.illumina.com/systems/array-scanners/iscan.html) microarrays. The tool merges VCF genotypes exported from [GenomeStudio](https://www.illumina.com/techniques/microarrays/array-data-analysis-experimental-design/genomestudio.html) with a second VCF, comprising genotypes derived from other samples and sources. Merging is based on matches of chromosome, position and certain conditions of major and minor alleles, with matched rows from each VCF concatenated into a single row (comprising all individuals) in the output files. The full algorithm is explained in the [accompanying manuscript](https://doi.org/10.3389/fevo.2021.629252), where we reported use of the human [Infinium Multi-Ethnic Global](https://www.illumina.com/products/by-type/microarray-kits/infinium-multi-ethnic-global.html) and [Infinium Omni 2.5](https://www.illumina.com/products/by-type/microarray-kits/infinium-omni25-8.html) arrays (hg19) to genotype great apes, and merged those with the genotypes of conspecifics previously published elsewhere.

## What's new since the paper came out?

#### Version 1.2
- Bug fixed to properly output VCF header, which had spurious line breaks on some Python versions.
- Output VCF contigs are now sorted in the order of the sequence dictionary, as pulled from the <reference_VCF>.
- The FORMAT column is restored with a GT value; this was causing output VCFs to fail GATK ValidateVariants.
- Upgraded deprecated pandas functions.

#### Version 1.1
- Bugs fixed to properly handle some multi-allelic sites.
- The reference population VCF file must now be [bgzipped and indexed with tabix](https://www.biostars.org/p/59492/). This requirement does not apply to the iScan VCF file, which can either be uncompressed or gzip compressed.
- In the prior version, the complete reference population VCF file was read into memory before the relevant records were pulled. This caused issues for some users handling enormous reference VCF files. In this version, we use the [Pysam](https://github.com/pysam-developers/pysam) library's lightweight wrapper of the [htslib C-API](http://www.ncbi.nlm.nih.gov/pubmed/19505943) to pull only the relevant records in the first place. The script should now run near-instantaneously, irrespective of input file size.
- Console output is now handled by the Python logging module and is written to a .log file in the output directory.
- Version numbering now follows 1.x vs 0.x format.

## Installation

iScanVCFMerge 1.2 requires Python 3.9. It has been successfully tested on MacOS Monterey 12.3.1 and CentOS Linux 7.9.2009.

Install the required packages first, if needed:

    python3 -m pip install pandas pysam

Clone from Github and execute:

    git clone "https://github.com/baneslab/iScanVCFMerge.git"
    cd iScanVCFMerge
    python3 iScanVCFMerge.py

Please note that the PyPi package is no longer maintained.

## Usage

    iScanVCFMerge [-h] -I <iScan_vcf> -R <reference_vcf> -O <output_directory>

Optional arguments:

    -h, --help                 Show the help message
    -I, --iScanVCF             Path to your iScan VCF file (.vcf or .vcf.gz)
    -R, --ReferenceVCF         Path to your reference VCF file, with which the iScan file will be merged. This must be bgzip compressed and be indexed with tabix
    -O, --output_directory     Name of the output directory (will be created if it doesn't exist)

## Citation

Please cite the use of this software as follows:

> Fountain, E. D., Zhou, L-C., Karklus, A., Liu, Q-X., Meyers, J., Fontanilla, I. K., Rafael, E. F., Yu, J-Y., Zhang, Q., Zhu, X-L., Pei, E-L., Yuan, Y-H. and Banes, G. L. (2021). Cross-species application of Illumina iScan microarrays for cost-effective, high-throughput SNP discovery. _Frontiers in Ecology and Evolution_, **9**:629252, doi: 10.3389/fevo.2021.629252.

The [Research Resource Identifier](https://www.force11.org/group/resource-identification-initiative) for iScanVCFMerge is [RRID:SCR_021193](https://scicrunch.org/resolver/RRID:SCR_021193).
