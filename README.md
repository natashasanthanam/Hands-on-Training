# Hands-on-Training



[workflowr]: https://github.com/jdblischak/workflowr

Running a Genotype Query using Bgenix

Use the following command to query ukbrest for variants on whichever chromosome and between whichever positions. Here we're querying on chromosome 17 at positions 46018872 and 46026674. This command will save the query in a bgen file
```
curl http://localhost:5000/ukbrest/api/v1.0/genotype/17/positions/46018872/46026674 \
  > pnpo_37.bgen
  ```

Next you have to index the bgen file 

```bgenix -g pnpo_37.bgen -index```

Finally convert the bgenix file to vcf

```bgenix -g pnpo_37.bgen | qctool -g - -filetype bgen -s /mnt/data/samples/ukb19526_imp_chr1_v3_s487395.sample -og ~/PNPO_37.vcf```
