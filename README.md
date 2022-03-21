# GEM2CHARGEGLI (Conversion tool from GEM output to meta-analysis-ready format for CHARGE GLI projects)

## Description
This python script is used to convert <a href="https://github.com/large-scale-gxe-methods/GEM">GEM</a> (v1.4.1 or later) output to the meta-analysis-ready format for Phase2 CHARGE Gene-Lifestyle Interactions projects. Please run using python2 (instead of python3; a python3 version is available <a href="https://github.com/pancong419/CHARGE-GLI">here</a>). You can check your python version using
```
python --version
```

## Usage
This python script reads GEM Model 1 and Model 2 output files, as well as a
SNP info file that includes the imputation flag (Genotyped/Imputed) and
quality measure (INFO), and writes the tab-delimited meta-analysis-ready file
in gzipped format. Missing values are coded as a period (.), the MAF cut-off
is 0.001, and the imputation quality (INFO) cut-off is 0.3.

If GEM was run separately by each chromosome, please only use the Model 1,
Model 2 and SNP info file names for chr22. The script assumes files for all
other 21 autosomes are located in the same directories respectively (but Model
1, Model 2 and SNP info files can be in different directories), with the same
naming convention. It will loop over starting from chr1, so there is no need
to specify 66 different input files.

Input files can be gzipped files (.gz).

## Input
`infile1`:
      Input file name of GEM Model 1 output. Example: Phase2.ARIC.AA.HDL.LTST.M1.COMBINED.chr22.out (for separate files by each chromosome), or Phase2.ARIC.AA.HDL.LTST.M1.COMBINED.all.out (one file for all results).
      
`infile2`:
      Input file name of GEM Model 2 output. Example: Phase2.ARIC.AA.HDL.LTST.M2.COMBINED.chr22.out (for separate files by each chromosome), or Phase2.ARIC.AA.HDL.LTST.M2.COMBINED.all.out (one file for all results).
      
`snpinfofile`:
      SNP info file name. It should at least contain the following information: SNPID, INFO, IMPUTED (see analysis plans). Example: chr22.info.gz (for separate files by each chromosome), or snpinfo.txt (one file for all results).
      
`outfile`:
      Output file name (without .gz). The results will be gzipped. Example: PHASE2.ARIC.AA.HDL.LTST.COMBINED.20220216.txt (the final gzipped output file would be PHASE2.ARIC.AA.HDL.LTST.COMBINED.20220216.txt.gz).
      
`Ename`:
      Variable name for the environmental exposure used in the gene-environment interaction analyses, as shown in your GEM output (NOTE: this is CaSE-senSItiVe). Example: LTST, STST, or ltst, stst.
      
`SNPIDname`:
      SNPID column name in your `snpinfofile`. Example: SNP.
      
`INFOname`:
      INFO column name in your `snpinfofile`. Example: Rsq.
      
`IMPUTEDname`:
      IMPUTED column name in your `snpinfofile`. Example: Genotyped.
      
`snpinfofile_delim`:
      Delimiter in your `snpinfofile`. Example: tab, space or , (comma).

## Example
```
python GEM2CHARGEGLI.py Phase2.ARIC.AA.HDL.LTST.M1.COMBINED.chr22.out Phase2.ARIC.AA.HDL.LTST.M2.COMBINED.chr22.out chr22.info.gz PHASE2.ARIC.AA.HDL.LTST.COMBINED.20220216.txt LTST SNP Rsq Genotyped tab
```

## Version
The current version is v0.2 (February 25, 2022).

## License
GPL-3.

## Contact
Please contact Han Chen (Han.Chen.2 AT uth.tmc.edu) if you have any questions.

## References
<p>If you use GEM in your analysis, please cite
<li>Westerman KE, Pham DT, Hong L, Chen Y, Sevilla-González M, Sung YJ, Sun YV, Morrison AC, Chen H, Manning AK. (2021) GEM: scalable and flexible gene-environment interaction analysis in millions of samples. <em>Bioinformatics</em> <b>37(20):</b>3514-3520. PubMed PMID: <a href="https://www.ncbi.nlm.nih.gov/pubmed/34695175">34695175</a>. PMCID: <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8545347/">PMC8545347</a>. DOI: <a href="https://doi.org/10.1093/bioinformatics/btab223">10.1093/bioinformatics/btab223</a>.</li></p>
