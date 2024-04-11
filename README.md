# A reminder：Peach genome annotation files have been updated in GDR
A reminder: Peach genome annotation files have been updated.

When I used the peach (Prunus persica) genome and the corresponding annotation file (Prunus persica Genome v2.0.a1, https://www.rosaceae.org/species/prunus_persica/genome_v2.0.a1) to run my RNAseq pipeline, I noticed that some genes disappeared from my raw gene expression counts matrix compare to using Phytozome database's peach genome and corresponding annotation file (Prunus persica v2.1, https://phytozome-next.jgi.doe.gov/) . Initially, I assumed these genes were not expressed. However, this assumption was incorrect; even if a gene is not expressed, it should show a value of 0 in the raw gene expression counts matrix rather than being absent.To investigate this issue, I check their annotation files. Interestingly, I found that these genes had exon information in Phytozome's annotation file but were absent in GDR's annotation file. This discrepancy explains why these genes could not be included in the calculation of gene expression counts due to the lack of exon information in GDR.

In my analysis, approximately 4,500 genes lacked exon information in GDR when compared to Phytozome. Then I wrote a letter to the GDR team to explain the problem.Finally,they made the "Ppersica_298_v2.1.gene.gff3.gz" file from Phytozome available in GDR under the name "Prunus_persica_v2.0.a1.gene_2015Update.gff3.gz.". However, since the file "Prunus_persica_v2.0.a1.gene_2015Update.gff3.gz" has just been uploaded to GDR and is also a 'Genes, CDS, 5' UTR, 3'UTR locations (GFF3 file)', which is the same type as the file listed above it, the only distinguishing factor in the names is '2015Update'. This may pose a challenge for users to determine which file to use based on the names alone. 

To avoid confusion, I suggest them to  report the problem in a prominent position on the GDR, but they did not reply and operate.

![image](https://github.com/changchuanjun/A_reminder_in_GDR/assets/155738984/8416e663-6633-40fd-ba60-ac05032dcc3d)

![image](https://github.com/changchuanjun/A_reminder_in_GDR/assets/155738984/4f8a750c-28ac-450e-8f07-27263c9a7cc1)

![image](https://github.com/changchuanjun/A_reminder_in_GDR/assets/155738984/b16ca7ad-4809-441b-83dc-40e3969b11e5)

