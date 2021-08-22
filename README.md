# iScanVCFMerge

iScanVCFMerge is a Python script to facilitate the cross-species application of [Illumina iScan system](https://www.illumina.com/systems/array-scanners/iscan.html) microarrays. The tool merges VCF genotypes exported from [GenomeStudio](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwiU08v-0MXyAhWWHM0KHczoAF0QFnoECAQQAQ&url=https%3A%2F%2Fwww.illumina.com%2Ftechniques%2Fmicroarrays%2Farray-data-analysis-experimental-design%2Fgenomestudio.html&usg=AOvVaw0c40T5Bip-n6ofC3v7NhFj) with a second VCF, comprising genotypes derived from other samples and sources. Merging is based on matches of chromosome, position and certain conditions of major and minor alleles, with matched rows from each VCF concatenated into a single row (comprising all individuals) in the output files. The full algorithm is explained in the [accompanying manuscript](https://doi.org/10.3389/fevo.2021.629252), where we reported use of the human [Infinium Multi-Ethnic Global](https://www.illumina.com/products/by-type/microarray-kits/infinium-multi-ethnic-global.html) and [Infinium Omni 2.5](https://www.illumina.com/products/by-type/microarray-kits/infinium-omni25-8.html) arrays (hg19) to genotype great apes, and merged those with the genotypes of conspecifics previously published elsewhere.

## What's new in version 1.1?
- Bugs fixed to properly handle some multi-allelic sites.
- Reference population VCF files are now converted to HDF5 on the fly, using `[vaex](https://vaex.io)` (versus `pandas`) for memory mapping, zero memory copying and lazy computations. This means that giant files can now be analysed, with disk space for temporary files being the limiting factor (versus memory).

## Installation

iScanVCFMerge 1.1 is currently being tested with Python 3.8.10 on MacOS Big Sur 11.4 and on Ubuntu 21.04.

### Option 1: Github clone and run with Python3

    git clone "https://github.com/baneslab/iScanVCFMerge.git"
    cd iScanVCFMerge
    python3 iScanVCFMerge.py

If running the script directly with Python, you may also need to install the required packages, _e.g._:

    python3 -m pip install pandas
    
### Run Option 2: Install with pip

    pip install iScanVCFMerge

or

    python3 -m pip install iScanVCFMerge

## Usage

    iScanVCFMerge [-h] -I <iScan_vcf> -R <reference_vcf> -O <output_directory>

Optional arguments:

    -h, --help                  Show the help message
    -R, --reference_vcf         Reference VCF file with which iScan file will be merged (.vcf or .vcf.gz)
    -I, --iScan_vcf             iScan VCF file  (.vcf or .vcf.gz)
    -O, --output_directory      Name of the output directory (will be created if it doesn't exist)

## Citation

Please cite the use of this software as follows:

> Fountain, E. D., Zhou, L-C., Karklus, A., Liu, Q-X., Meyers, J., Fontanilla, I. K., Rafael, E. F., Yu, J-Y., Zhang, Q., Zhu, X-L., Pei, E-L., Yuan, Y-H. and Banes, G. L. (2021). Cross-species application of Illumina iScan microarrays for cost-effective, high-throughput SNP discovery. Frontiers in Ecology and Evolution, 9:629252, doi: 10.3389/fevo.2021.629252.
