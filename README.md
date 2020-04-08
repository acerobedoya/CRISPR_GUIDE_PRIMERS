# CRISPR_GUIDE_PRIMERS

This program can have a long run time, recommend turning computer sleep OFF and leaving it alone 
to avoid accidently clicking and disrupting the run; because of this, internet speed may affect process.
The SHAM row and duplicate of the first row ensure all inputs get an output despite slower interenet.
This program relies on the use of selenium webdriver.

Purpose: this tool creates primers targeting genomic areas around CRISPR guides (200bp around cutsite) allowing for amplification of segments that can be used for subsequent sequencing to indentify of specific indels resulting from CRISPR screens.

Takes a csv with guide sequences, 

runs through UCSC genome browser: 
https://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&lastVirtModeType=default&lastVirtModeExtraState=&virtModeType=default&virtMode=0&nonVirtPosition=&position=chr7%3A127685612%2D127687611&hgsid=818198291_7kjxM2ogVXHZPH94SJesF50914dy

to obtain 2000bp genomic location around guide (ie "chr7:5,528,404-5,530,403")
-some guides do not return a match and are designed a value of "NA," other guides return multiple matches usually depicted with a "K" strng included
-NA and K containing Genomic Locations are removed and stored into a "guides_fail" list and output into a text file to be done by hand

and runs it through primer BLAST:
https://www.ncbi.nlm.nih.gov/genome/gdv/browser/genome/?id=GCF_000001405.39  #Tools dropdown for Primer BLAST option


with specific parameters:
-adjusts product size to 500-1000
-changes reference genome
-adjusts forward and reverse to creat 200bp buffer zone around CRISPR cut zone

and extracts the first primer pair from results (ie):
https://www.ncbi.nlm.nih.gov/tools/primer-blast/primertool.cgi?ctg_time=1585801635&job_key=f3Wgd83kwEzndlBzXRN0QScIZXMKG35uCw


Downloads:
selenium instructions: https://selenium-python.readthedocs.io/installation.html
chromedriver: https://chromedriver.chromium.org/downloads

