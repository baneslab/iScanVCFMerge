# iScanVCFMerge

## Citation
Fountain, E. D., Zhou, L., Liu, Q., Karklus, A., Meyers, J., Fontanilla, I. K. C., Rafael, N., Pei, E., Yu, J., Zhang, Q., Zhu, X., Yuan, Y. and Banes, G. L. (2021). Cross-species application of Illumina iScan microarrays for cost-effective,high-throughput SNP discovery. Frontiers in Ecology and Evolution.
                
## Installation

pip install iScanVCFMerge

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
