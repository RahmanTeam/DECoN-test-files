# DECoN-test-files
Files to be used for testing an installation of DECoN
If it's not already available, you will need to download and unzip the reference genome FASTA file called human_g1k_v37.fasta from http://ftp.1000genomes.ebi.ac.uk/vol1/ftp/technical/reference/

On Mac/linux, run the below commands, replacing "/path/to/" with the correct file paths
cd /path/to/DECoN
Rscript ReadInBams.R --bams DECoN-test-files-1.0.0 --bed /path/to/DECoN-test-files-1.0.0/test_Target_Regions.bed --fasta /path/to/human_g1k_v37.fasta --out test
Rscript IdentifyFailures.R --Rdata test.RData --exons /path/to/DECoN-test-files-1.0.0/test_customNumbering.txt --custom TRUE --out testFailures
Rscript makeCNVcalls.R --Rdata test.RData --exons /path/to/DECoN-test-files-1.0.0/test_customNumbering.txt --custom TRUE --out testCalls --plot All --plotFolder testPlots
Rscript runShiny.R --Rdata testCalls.RData

On Windows, run each file and follow the prompts
ReadInBams.bat
IdentifyFailures.bat
makeCNVcalls.bat
gui.bat

This will generate the files test.RData, testFailures_Failures.txt, testCalls.RData, testCalls_all.txt, testCalls_custom.txt, a folder called testPlots, and a file in testPlots called 207_BRCA1.pdf.
