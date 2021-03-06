# vcfReadDepther
Simple utility that estimates the variant density of a VCF file using only the .tbi index file

## Usage
```
cat 1.vcf.gz.tbi | ./vcfReadDepther
```

## Output
The output is in a simple format that makes it easy to parse when streaming. In the example below each #Number indicates a sequence with the number being the reference id. Following the reference id are a series of values each of which corresponding to a 16384 nucleotide bin. The first bin will be from nucleotide position 0-16384 and the next bin will be from nucleotide position 16385-32769 and so on. The values are the amount of bytes needed in the VCF file to store all the records that fall in a particular bin. For example the first bin in reference #1 below has reads that take up 1200 bytes of disk space, *not* 1200 VCF records. However the relationship between records and byte space is very good and we can see where the density is high and low even if we don't know the corresponding density (number of VCF records) for any particular point.
```
#1
1200
1104
1238
4329
3298
3249
2293
3293
4345
3450
#2
1200
1104
1238
4329
3298
3249
2293
3293
4345
3450
```