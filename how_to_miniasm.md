```map-pb```or ```map-ont``` for mapping to an existing reference (either pacbio or nanopore data)

```ava-pb```or ```ava-ont```for read overlap

first minimap2
```
#!/bin/bash
date
 ../minimap2/./minimap2 -x ava-ont -t8 ../miniasm_assembly/results/Dere_14062023_PAO93669_sorted_150x.fastq.gz ../miniasm_assembly/results/Dere_14062023_PAO93669_sorted_150x.fastq.gz | gzip -1 > ../minimap_output/minimap.paf.gz
date
```

then miniasm
```
#!/bin/bash
date
../miniasm/./miniasm -f /results/Dere_14062023_PAO93669_sorted_150x.fastq.gz /home/sarah/minimap_output/minimap.paf.gz > miniasm.gfa
date
```
then create a .fasta file from the .gfa file
```
awk '/^S/{print ">"$2"\n"$3}' miniasm.gfa > miniasm.fasta
```
check how any contigs are there:
```
grep '>' miniasm.fasta | wc -l
```
