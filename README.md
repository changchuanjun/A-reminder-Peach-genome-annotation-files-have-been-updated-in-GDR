# A reminder：A peach genome annotation file has been updated in GDR(Genome Database for Rosaceae,https://www.rosaceae.org/)
A reminder: A peach genome annotation file(Prunus persica Genome v2.0.a1) has been updated.

When I used the peach (Prunus persica) genome and the corresponding annotation file (Prunus persica Genome v2.0.a1, https://www.rosaceae.org/species/prunus_persica/genome_v2.0.a1) to run my RNAseq pipeline, I noticed that some genes disappeared from my raw gene expression counts matrix compare to using Phytozome database's peach genome and corresponding annotation file (Prunus persica v2.1, https://phytozome-next.jgi.doe.gov/) . Initially, I assumed these genes were not expressed. However, this assumption was incorrect; even if a gene is not expressed, it should show a value of 0 in the raw gene expression counts matrix rather than being absent.To investigate this issue, I check their annotation files. Interestingly, I found that these genes had exon information in Phytozome's annotation file but were absent in GDR's annotation file. This discrepancy explains why these genes could not be included in the calculation of gene expression counts due to the lack of exon information in GDR.

In my analysis, approximately 4,500 genes lacked exon information in GDR when compared to Phytozome. I found that some of these genes also had functions (such as transcription factors), and that these genes were randomly distributed across chromosomes rather than concentrated on a single chromosome.The missing genes in raw gene expression counts matrix, especially if they include important functional genes like transcription factors, could have significant implications for downstream analysis. Their absence might affect pathway analysis, regulatory network inference, and potentially lead to overlooking important biological insights.

Then I wrote a letter to the GDR team to explain the problem.Finally,they made the "Ppersica_298_v2.1.gene.gff3.gz" file from Phytozome available in GDR under the name "Prunus_persica_v2.0.a1.gene_2015Update.gff3.gz.". 

I speculate that it is likely that the previous annotation file(Prunus_persica_v2.0.a1.gene.gff3.gz) in GDR was also sourced from Phytozome. However, Phytozome released an updated annotation file in 2015(Ppersica_298_v2.1.gene.gff3.gz), which included additional exon information for approximately 4500 genes. Unfortunately, GDR did not take note of this update by Phytozome and continued to use the old file.

However, since the file "Prunus_persica_v2.0.a1.gene_2015Update.gff3.gz" has just been uploaded to GDR and is also a 'Genes, CDS, 5' UTR, 3'UTR locations (GFF3 file)', which is the same type as the file listed above it, the only distinguishing factor in the names is '2015Update'. This may pose a challenge for users to determine which file to use based on the names alone. 

For files of the 'Genes, CDS, 5' UTR, 3'UTR locations (GFF3 file)' type, 'Prunus_persica_v2.0.a1.gene_2015Update.gff3.gz' is recommended as the first choice.(https://www.rosaceae.org/rosaceae_downloads/Prunus_persica/Prunus_persica-genome.v2.0.a1/genes/Ppersica_298_v2.1.gene_exons.gff3.gz)


In addition, I speculated that probably many researchers had met the same question when used the RNAseq techology to conduct scientific research using GDR's genome and previous annotation file, but if they didn't use the Phytozome database for peach's genome files and annotated files, they may not have noticed the problem. if they also miss the expression information of these genes, there is a risk that the expression information of genes in some regulatory pathways will be missed, and even new genes will not be mined. I hope people can pay attention to this problem.

![image](https://github.com/changchuanjun/A_reminder_in_GDR/assets/155738984/8416e663-6633-40fd-ba60-ac05032dcc3d)

![image](https://github.com/changchuanjun/A_reminder_in_GDR/assets/155738984/4f8a750c-28ac-450e-8f07-27263c9a7cc1)

![image](https://github.com/changchuanjun/A_reminder_in_GDR/assets/155738984/b16ca7ad-4809-441b-83dc-40e3969b11e5)

Additional information:
1、my RNAseq pipeline process:
The raw sequencing data were quality-controlled using fastp (version 0.22.0) with the default settings. Subsequently, the filtered reads were aligned to the reference genome using HISAT2 (version 2.2.1) with default parameters. The resulting SAM file, containing the aligned reads, was converted to BAM format, sorted, and indexed with SAMtools (version 1.18). Gene expression counts were extracted from the BAM files using featureCounts (version 1.6.2).
 
2、some genes do not have the exon formation

Prupe.1G000200
Prupe.1G000500
..............
---------------------------------------------------
