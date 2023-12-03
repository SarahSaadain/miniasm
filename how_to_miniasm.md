```map-pb```or ```map-ont``` for mapping to an existing reference (either pacbio or nanopore data)

```ava-pb```or ```ava-ont```for read overlap

first minimap2
```
./minimap2 -x ava-ont -t8 ../miniasm_assembly/results/Dere_14062023_PAO93669_sorted_150x.fastq.gz ../miniasm_assembly/results/Dere_14062023_PAO93669_sorted_150x.fastq.gz | gzip -1 > ../minimap_output/minimap.paf.gz
```

then miniasm
```
./miniasm -f ../miniasm_assembly/results/Dere_14062023_PAO93669_sorted_150x.fastq.gz ../minimap_output/minimap.paf.gz > ./miniasm_assembly/miniasm.gfa
```
