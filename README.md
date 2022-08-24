# HQGR
The High Quality Reads Generator (HQGR) script is provided to implement second round of CCS for long amplicon HiFi sequencing. 

Please cite the dependencies if used:
* MAFFT: [Katoh, K., & Standley, D. M. (2013). MAFFT Multiple Sequence Alignment Software Version 7: Improvements in Performance and Usability. Mol Biol Evol, 30(4), 772-780.](https://pubmed.ncbi.nlm.nih.gov/23329690/)
* EMBOSS: [Rice, P., Longden, I., & Bleasby, A. (2000). EMBOSS: the European Molecular Biology Open Software Suite. Trends Genet, 16(6), 276-277.](https://pubmed.ncbi.nlm.nih.gov/10827456/)

# Quick start guide
HQGR is currently maintained under Python 3.8.12, but designed to be compatible with version higher than 3. 
* For `Linux`: you need install `EMBOSS` and `MAFFT` first as below:

[EMBOSS](http://emboss.sourceforge.net/download/) install: If you are compiling a fresh installation:
```
./configure
make
```
If you compile it on subsequent occasions, use the following:-
```
rm config.cache
make clean
./configure
make
```
`MAFFT` software install refer to [here.](https://mafft.cbrc.jp/alignment/software/linux.html)
After installation, adding path to HQGR by parameters `-MAd` and `-CoAd` as descript below to use.

* For `Windows`: you just need to install `EMBOSS` for window version in anywhere you want and you don't need adding `cons` path to HQGR, carry out by default setting.

# Usage
Python HQGR.py [option].

# Required parameters
```
* -i     --sequencepath  : input file, fasta format was required.
* -o     --Outputpath    : output file directory.
* -d     --primerpath    : barcode sequences information for demultiplexing, can be combined with primer sequences.
* -fl    --frblen        : the length of forward barcode sequence for demultiplexing.
* -bl    --beblen        : the length of reverse barcode sequence for demultiplexing.
* -min   --min           : filtering minimum reads in length, default=0.
* -max   --max           : filtering maximum reads in length, default=100000.
* -MAd   --MafftAddress  : specified `Mafft` path for Linux platform.
* -CoAd  --ConsAddress   : specified `cons` path for Linux platform.
```
# Barcode format
Barcode format was descripted below:
```
>F1_A701_5p
ATCACGACGCTAGGA
>F1_A702_5p
ACAGTGGTGCTAGGA
>R1_A504_3p
TAAGACACAGCTGCG
>R1_A505_3p
CTAATGGACCTTTCG
```
All sequences direction were 5'→3'. Forward sequence was identified by `_5p`, reverse sequence was identified by `_3p`.

# Example
Following below commond for test:
```
$ python HQGR.py -i ./example/ccs.fa -d ./example/barcode.fasta -min 8000 -max 9000 -fl 36 -b1 23 -o ./subread
```

# Contact
Questions and suggestions are welcome, feel free to contact: Caizhengfei686@qq.com
