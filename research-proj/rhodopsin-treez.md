#Notes from lizzy's old notes on ways to use hmmer to align new sequences to an existing alignment

```
hmmbuild pr.arbNames.hmm pr.arbNames.stockholm
hmmalign --mapali pr.arbNames.stockholm pr.arbNames.hmm env_blastp_NQ.faa > pr.arbNames.env_blastp.stk
FastTree -wag pr.arbNames.env_blastp.aln.faa > pr.arbNames.env_blastp.Fast.tre
```
