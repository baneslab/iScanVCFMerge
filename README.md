# iScanVCFMerge
        
## Run Option 1: Github clone and run with Python3

    git clone "https://github.com/baneslab/iScanVCFMerge.git"
    $ cd iScanVCFMerge
    $ python3 iScanVCFMerge.py

## Run Option 2: Install with pip

    pip install iScanVCFMerge

or

   python3 -m pip install iScanVCFMerge

## Usage

iScanVCFMerge [-h] -R REFERENCE_VCF -I ISCAN_VCF -O OUTPUT_DIRECTORY

optional arguments:
  -h, --help            show this help message and exit
  -R REFERENCE_VCF, --reference_vcf REFERENCE_VCF
                        Path to your reference VCF file (.vcf or .vcf.gz)
  -I ISCAN_VCF, --iScan_vcf ISCAN_VCF
                        Path to your iScan VCF file (.vcf or .vcf.gz)
  -O OUTPUT_DIRECTORY, --output_directory OUTPUT_DIRECTORY
                        Name of the output directory


## Citation

Please cite as:

> Fountain, E. D., Zhou, L-C., Liu, Q-X., Karklus, A., Meyers, J., Fontanilla, I. K., Rafael, N., Pei, E-L., Yu, J-Y., Zhang, Q., Zhu, X-L., Yuan, Y-H. and Banes, G. L. (2021). Cross-species application of Illumina iScan microarrays for cost-effective, high-throughput SNP discovery. Frontiers in Ecology and Evolution, doi: 10.3389/fevo.2021.629252
