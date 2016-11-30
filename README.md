# GutV3V4_mothur
Project Workflow and Log for 16s rRNA Metagenomic analysis of Human gut for V3V4 region

Workflow was carried out refering Mothur MiSeqSOP
https://www.mothur.org/wiki/MiSeq_SOP

#Reference Used
Silva  silva.nr_v123.align cutomised for the primer specific to the project, using the method mentioned here http://blog.mothur.org/2016/07/07/Customization-for-your-region/. 

Forward 5’-ACTCCTACGGGAGGCAGCAG-3’

Reverse 5’-GGACTACHVGGGTWTCTAAT-3’

#stability.files

Sample-01_S1	Sample-01_S1_L001_R1_001.fastq	Sample-01_S1_L001_R2_001.fastq
Sample-02_S2	Sample-02_S2_L001_R1_001.fastq	Sample-02_S2_L001_R2_001.fastq
Sample-03_S3	Sample-03_S3_L001_R1_001.fastq	Sample-03_S3_L001_R2_001.fastq
Sample-04_S4	Sample-04_S4_L001_R1_001.fastq	Sample-04_S4_L001_R2_001.fastq
Sample-05_S5	Sample-05_S5_L001_R1_001.fastq	Sample-05_S5_L001_R2_001.fastq
Sample-06_S6	Sample-06_S6_L001_R1_001.fastq	Sample-06_S6_L001_R2_001.fastq
Sample-07_S7	Sample-07_S7_L001_R1_001.fastq	Sample-07_S7_L001_R2_001.fastq
Sample-08_S8	Sample-08_S8_L001_R1_001.fastq	Sample-08_S8_L001_R2_001.fastq
Sample-09_S9	Sample-09_S9_L001_R1_001.fastq	Sample-09_S9_L001_R2_001.fastq
Sample-10_S10	Sample-10_S10_L001_R1_001.fastq	Sample-10_S10_L001_R2_001.fastq
Sample-11_S11	Sample-11_S11_L001_R1_001.fastq	Sample-11_S11_L001_R2_001.fastq
Sample-12_S12	Sample-12_S12_L001_R1_001.fastq	Sample-12_S12_L001_R2_001.fastq
Sample-13_S13	Sample-13_S13_L001_R1_001.fastq	Sample-13_S13_L001_R2_001.fastq
Sample-14_S14	Sample-14_S14_L001_R1_001.fastq	Sample-14_S14_L001_R2_001.fastq
Sample-15_S15	Sample-15_S15_L001_R1_001.fastq	Sample-15_S15_L001_R2_001.fastq
Sample-16_S16	Sample-16_S16_L001_R1_001.fastq	Sample-16_S16_L001_R2_001.fastq
Sample-17_S17	Sample-17_S17_L001_R1_001.fastq	Sample-17_S17_L001_R2_001.fastq
Sample-18_S18	Sample-18_S18_L001_R1_001.fastq	Sample-18_S18_L001_R2_001.fastq
Sample-19_S19	Sample-19_S19_L001_R1_001.fastq	Sample-19_S19_L001_R2_001.fastq
Sample-20_S20	Sample-20_S20_L001_R1_001.fastq	Sample-20_S20_L001_R2_001.fastq
Sample-21_S21	Sample-21_S21_L001_R1_001.fastq	Sample-21_S21_L001_R2_001.fastq
Sample-22_S22	Sample-22_S22_L001_R1_001.fastq	Sample-22_S22_L001_R2_001.fastq
Sample-26_S23	Sample-26_S23_L001_R1_001.fastq	Sample-26_S23_L001_R2_001.fastq
Sample-27_S24	Sample-27_S24_L001_R1_001.fastq	Sample-27_S24_L001_R2_001.fastq

#make.contigs
make.contigs(file=stability.files, processors=14)

Output File Names: 
stability.trim.contigs.fasta
stability.trim.contigs.qual
stability.contigs.report
stability.scrap.contigs.fasta
stability.scrap.contigs.qual
stability.contigs.groups

#Summary.seqs
		Start	End	NBases	Ambigs	Polymer	NumSeqs
Minimum:	1	251	251	0	3	1
2.5%-tile:	1	444	444	0	4	42524
25%-tile:	1	446	446	0	5	425239
Median: 	1	464	464	0	5	850477
75%-tile:	1	469	469	0	5	1275715
97.5%-tile:	1	470	470	2	6	1658429
Maximum:	1	502	502	49	251	1700952
Mean:	1	457.173	457.173	0.216084	5.03002
# of Seqs:	1700952

Output File Names: 
stability.trim.contigs.summary

#Screen.seqs

screen.seqs(fasta=stability.trim.contigs.fasta,group=stability.contigs.groups,maxambig=0,maxlength=470)

Output File Names: 
stability.trim.contigs.good.fasta
stability.trim.contigs.bad.accnos
stability.contigs.good.groups

Post screen summary

		Start	End	NBases	Ambigs	Polymer	NumSeqs
Minimum:	1	251	251	0	3	1
2.5%-tile:	1	444	444	0	4	37479
25%-tile:	1	446	446	0	5	374789
Median: 	1	464	464	0	5	749577
75%-tile:	1	469	469	0	5	1124365
97.5%-tile:	1	470	470	0	6	1461675
Maximum:	1	470	470	0	122	1499153
Mean:	1	457.095	457.095	0	4.97581
# of Seqs:	1499153

#Unique.seqs()
unique.seqs(fasta=stability.trim.contigs.good.fasta)

Output File Names: 
stability.trim.contigs.good.names
stability.trim.contigs.good.unique.fasta

count.seqs(name=stability.trim.contigs.good.names, group=stability.contigs.good.groups)
summary.seqs(count=stability.trim.contigs.good.count_table)

Summary after unique.seq
		Start	End	NBases	Ambigs	Polymer	NumSeqs
Minimum:	1	251	251	0	3	1
2.5%-tile:	1	444	444	0	4	37479
25%-tile:	1	446	446	0	5	374789
Median: 	1	464	464	0	5	749577
75%-tile:	1	469	469	0	5	1124365
97.5%-tile:	1	470	470	0	6	1461675
Maximum:	1	470	470	0	122	1499153
Mean:	1	457.095	457.095	0	4.97581
# of unique seqs:	1071664
total # of seqs:	1499153

#Align.seqs()
align.seqs(fasta=stability.trim.contigs.good.unique.fasta, reference=silva.nr_v123_V3-V4.align)

Output File Names: 
stability.trim.contigs.good.unique.align
stability.trim.contigs.good.unique.align.report
stability.trim.contigs.good.unique.flip.accnos

Summary.seqs of aligned read
		Start	End	NBases	Ambigs	Polymer	NumSeqs
Minimum:	0	0	0	0	1	1
2.5%-tile:	2	17016	403	0	4	37479
25%-tile:	2	17016	404	0	4	374789
Median: 	2	17016	422	0	5	749577
75%-tile:	2	17016	427	0	5	1124365
97.5%-tile:	2	17016	428	0	6	1461675
Maximum:	17016	17016	450	0	122	1499153
Mean:	37.5503	16987.7	413.902	0	4.95173
# of unique seqs:	1071664
total # of seqs:	1499153

Output File Names: 
stability.trim.contigs.good.unique.summary

It took 52 secs to summarize 1499153 sequences.

#Screen.seqs
screen.seqs(fasta=stability.trim.contigs.good.unique.align, count=stability.trim.contigs.good.count_table, summary=stability.trim.contigs.good.unique.summary,start=2,end=17016,maxhomop=8)

Output File Names: 
stability.trim.contigs.good.unique.good.summary
stability.trim.contigs.good.unique.good.align
stability.trim.contigs.good.unique.bad.accnos
stability.trim.contigs.good.good.count_table

Summary
		Start	End	NBases	Ambigs	Polymer	NumSeqs
Minimum:	1	17016	380	0	3	1
2.5%-tile:	2	17016	403	0	4	37202
25%-tile:	2	17016	404	0	4	372020
Median: 	2	17016	422	0	5	744039
75%-tile:	2	17016	427	0	5	1116058
97.5%-tile:	2	17016	428	0	6	1450875
Maximum:	2	17016	450	0	8	1488076
Mean:	2	17016	415.438	0	4.94867
# of unique seqs:	1060591
total # of seqs:	1488076

Output File Names: 
stability.trim.contigs.good.unique.good.summary

#Filter.seqs()
filter.seqs(fasta=stability.trim.contigs.good.unique.good.align, vertical=T, trump=.)

Length of filtered alignment: 1064
Number of columns removed: 15952
Length of the original alignment: 17016
Number of sequences used to construct filter: 1060591

Output File Names: 
stability.filter
stability.trim.contigs.good.unique.good.filter.fasta

#Unique.seqs()
unique.seqs(fasta=stability.trim.contigs.good.unique.good.filter.fasta,count=stability.trim.contigs.good.good.count_table)

Output File Names: 
stability.trim.contigs.good.unique.good.filter.count_table
stability.trim.contigs.good.unique.good.filter.unique.fasta

#precluster

pre.cluster(fasta=stability.trim.contigs.good.unique.good.filter.unique.fasta,count=stability.trim.contigs.good.good.count_table,diffs=2)

Total number of sequences before pre.cluster was 5553.
pre.cluster removed 2428 sequences.

It took 2 secs to cluster 5553 sequences.
It took 71 secs to run pre.cluster.

Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.fasta
stability.trim.contigs.good.unique.good.filter.unique.precluster.count_table
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-01_S1.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-02_S2.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-03_S3.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-04_S4.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-05_S5.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-06_S6.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-07_S7.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-08_S8.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-09_S9.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-10_S10.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-11_S11.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-12_S12.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-13_S13.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-14_S14.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-15_S15.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-16_S16.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-17_S17.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-18_S18.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-19_S19.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-20_S20.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-21_S21.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-22_S22.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-26_S23.map
stability.trim.contigs.good.unique.good.filter.unique.precluster.Sample-27_S24.map

#chimer.uchime

chimera.uchime(fasta=stability.trim.contigs.good.unique.good.filter.unique.precluster.fasta,reference=silva.gold.align,dereplicate=T)

remove.seqs(fasta=stability.trim.contigs.good.unique.good.filter.unique.precluster.fasta, accnos=stability.trim.contigs.good.unique.good.filter.unique.precluster.ref.uchime.accnos)

Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.fasta

Summary
		Start	End	NBases	Ambigs	Polymer	NumSeqs
Minimum:	1	1064	383	0	3	1
2.5%-tile:	1	1064	403	0	4	37202
25%-tile:	1	1064	423	0	5	372020
Median: 	1	1064	450	0	8	744039
75%-tile:	1	1064	383	0	3	1116058
97.5%-tile:	1	1064	383	0	3	1450875
Maximum:	1	1064	450	0	8	1488076
Mean:	0.420637	447.558	175.058	0	2.09262
# of unique seqs:	94490
total # of seqs:	1488076

Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.summary

#Classify.seqs()

classify.seqs(fasta=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.fasta, count=stability.trim.contigs.good.unique.good.filter.unique.precluster.count_table,reference=silva.nr_v123_V3-V4.align, taxonomy=silva.nr_v123.tax, cutoff=80)

It took 10 secs to create the summary file for 94490 sequences.


Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.taxonomy
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.tax.summary

remove.lineage(fasta=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.fasta, count=stability.trim.contigs.good.unique.good.filter.unique.precluster.count_table,taxonomy=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.taxonomy, taxon=Chloroplast-Mitochondria-unknown-Archaea-Eukaryota)

Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.taxonomy
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.pick.fasta
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.count_table

 summary.tax(taxonomy=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.taxonomy,count=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.count_table)
 
 Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.tax.summary

#Phylotype
phylotype(taxonomy=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.taxonomy)


Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.tx.sabund
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.tx.rabund
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.tx.list







#Alt way
chimera.uchime(fasta=stability.trim.contigs.good.unique.good.filter.unique.precluster.fasta,count=stability.trim.contigs.good.unique.good.filter.unique.precluster.count_table,dereplicate=t,processors=15)

Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.denovo.uchime.pick.count_table
stability.trim.contigs.good.unique.good.filter.unique.precluster.denovo.uchime.chimeras
stability.trim.contigs.good.unique.good.filter.unique.precluster.denovo.uchime.accnos

remove.seqs(fasta=stability.trim.contigs.good.unique.good.filter.unique.precluster.fasta,accnos=stability.trim.contigs.good.unique.good.filter.unique.precluster.denovo.uchime.accnos)
Removed 27011 sequences from your fasta file.

Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.fasta

		Start	End	NBases	Ambigs	Polymer	NumSeqs
Minimum:	1	1064	383	0	3	1
2.5%-tile:	1	1064	403	0	4	36377
25%-tile:	1	1064	450	0	8	363762
Median: 	1	1064	383	0	3	727523
75%-tile:	1	1064	383	0	3	1091284
97.5%-tile:	1	1064	383	0	3	1418669
Maximum:	1	1064	450	0	8	1455045
Mean:	0.147402	156.835	61.4083	0	0.730143
# of unique seqs:	90487
total # of seqs:	1455045


classify.seqs(fasta=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.fasta,count=stability.trim.contigs.good.unique.good.filter.unique.precluster.denovo.uchime.pick.count_table,reference=silva.nr_v123_V3-V4.align,taxonomy=silva.nr_v123.tax,cutoff=80)

It took 583 secs to classify 90487 sequences.


It took 10 secs to create the summary file for 90487 sequences.


Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.taxonomy
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.tax.summary

remove.lineage(fasta=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.fasta, count=stability.trim.contigs.good.unique.good.filter.unique.precluster.denovo.uchime.pick.count_table, taxonomy=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.taxonomy,taxon=Chloroplast-Mitochondria-unknown-Archaea-Eukaryota)

[NOTE]: The count file should contain only unique names, so mothur assumes your fasta, list and taxonomy files also contain only uniques.


Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.taxonomy
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.pick.fasta
stability.trim.contigs.good.unique.good.filter.unique.precluster.denovo.uchime.pick.pick.count_table

summary.tax(taxonomy=current, count=current)
Using stability.trim.contigs.good.unique.good.filter.unique.precluster.denovo.uchime.pick.pick.count_table as input file for the count parameter.
Using stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.taxonomy as input file for the taxonomy parameter.
reftaxonomy is not required, but if given will keep the rankIDs in the summary file static.

It took 8 secs to create the summary file for 90337 sequences.


Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.tax.summary

phylotype(taxonomy=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.taxonomy)
1
2
3
4
5
6

Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.tx.sabund
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.tx.rabund
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.tx.list

classify.otu(list=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.tx.list,count=stability.trim.contigs.good.unique.good.filter.unique.precluster.denovo.uchime.pick.pick.count_table,taxonomy=stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.taxonomy,label=1)
reftaxonomy is not required, but if given will keep the rankIDs in the summary file static.
1	452

Output File Names: 
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.tx.1.cons.taxonomy
stability.trim.contigs.good.unique.good.filter.unique.precluster.pick.nr_v123.wang.pick.tx.1.cons.tax.summary

