# Instructions for running mothur on 16S rRNA sequencing of the v4 region.

**Finding region coordinates.**

Prior to running the pipeline, find the coordinate for your region. I will show you how to do this for the v4v5 region.
1) Locate your forward and reverse primers. Replace degenerates with any base pair option. 
  
  Ex. 
      
      > forward (w/ degenerates)= GTGYCAGCMGCCGCGGTAA
      > forward (w/out degenerates)= GTGCCAGCAGCCGCGGTAA
      
      > reverse_806r (w/ degenerates)= GGACTACNVGGGTWTCTAAT
      > reverse_806r (w/out degenerates)= GGACTACAGGGGTATCTAAT
      
2) Find the reverse complement of your reverse primer. To do this, first find the complemenent of your reverse primer.     
    > GGACTACAGGGGTATCTAAT (reverse primer)
    
    > CCTGATGTCCCCATAGATTA (complement of reverse primer)
    
    Next find the reverse of this complement. 
    
    > ATTAGATACCCCTGTAGTCC (reverse of the complement of the reverse primer)
    
    Save this for later use.
3) Go to https://www.ncbi.nlm.nih.gov/tools/primer-blast/
4) Input your forward and reverse primers into the boxes labeled "Use my own forward primer (5'->3' on plus strand)" and "Use my own reverse primer (5'->3' on minus strand)".
5) Scroll down to the heading "Primer Pair Specificity Checking Parameters" and change the database setting "nr". 
6) Below that, change the organism setting to "Escherichia coli (taxid:562)".
7) Click "Get Primers".
8) In a line that looks similiar to the following:
   >CP101983.1 Escherichia coli strain STEC1096 chromosome, complete genome
   
   copy the alphanumeric cominbation up to the dot. In this case, that would be CP101983.
9) Go to https://www.ncbi.nlm.nih.gov/ and copy this string into the search bar.
10) Click on the result and then select "fasta".
11) Use ctrl/command + f to locate your forward primer. Start there and then copy the ~400-500 pairs that follow and paste into a text editor.
12) Use ctrl/command + f to locate your reverse complement primer within this text. Some of the sequences may be mismatched, so try searching for different sections of the primer if you cannot find the whole one at first.
13) Once you locate the reverse complement primer, check the length of the section from the forward primer to there. It would be around 300 base pairs. Copy this section over to a file called ecoliv4.fasta. You will need this eventually in the pipeline.


**Downloading reference files**
1) Go to https://mothur.org/wiki/silva_reference_files/
2) Download the latest version of the files called "full-length sequence and taxonomy database" and "seed database file", move them your working directory, and unzip them. This should generate 4 files whose names will vary slightly depending on the version downloaded: 

> silva.nr_v138_1.tax
> silva.nr_v138_1.align
> silva.seed_v138_1.tax
> silva.seed_v138_1.align
