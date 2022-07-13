# Welcome to the Shasta User Guides

## Background

Shasta is a de novo genome assembly tool for Oxford Nanopore sequencing reads initiated as a collaboration between the [Chan Zuckerberg Initiative](https://chanzuckerberg.com/) and the [Computational Genomics Lab](https://cglgenomics.ucsc.edu/) at the UC Santa Cruz Genomics Institute ([Shafin et al. 2020](https://doi.org/10.1038/s41592-021-01299-w)). 

Shasta is at the leading edge of cost and performance efficiency. A human genome can be assembled in ~3 hrs for ~$10 of compute costs. And recent benchmarking shows that Shasta produces higher quality human assemblies than the leading competitor Flye ([Shafin et al. 2021](https://doi.org/10.1038/s41587-020-0503-6)). The newest version of Shasta can phase diploid genomes, resolving haplotypes in humans across ~90% of the genome.

## What kinds of science is Shasta enabling?
*Shasta Team (CZI, UC Santa Cruz) has direct involvement in projects.*

### Diagnose genetic diseases

**[Ultra-rapid human genome sequencing in critical care settings](https://doi.org/10.1038/s41587-022-01221-5)**

*Stanford University, UC Santa Cruz, Baylor University, Google, Oxford Nanopore Technologies, NVIDA*

- Researchers developed an ultra-rapid (<8 hr) genome sequencing and analysis pipeline twice as fast as previous approaches.

- Applied to diagnose two critically ill patients, a 57-year-old man and a 14-month-old infant.

- Used Shasta to fine-tune structural variant calls with local assembly of reads.

**Development of nanopore sequencing and Shasta assembly to clarify rare disease diagnosis**

*UC Santa Cruz, Broad Institute, Children's National Hopsital, CZI*

- Attempt to solve undiagnosed rare genetic disorders in patients where current approaches (i.e., short-read genome assembly, exome sequencing, cytogenetics) fail.

- Use ONT long-read sequencing and Shasta to de novo assemble genomes of patients with unsolved cases.

### Study genetic basis of common diseases

[NIH Intramural Center for Alzheimer’s and Related Dementias (CARD) - long-read sequencing](https://card.nih.gov/research-programs/long-read-sequencing)

*NIH, UC Santa Cruz, CZI*

- Build a public database of long-read sequence data, including genome assemblies of people with Alzheimer’s and related dementias and healthy individuals.

- Assembly at scale: 4,000 genomes with Shasta using a single flow cell's worth of reads per sample.

### Discover human genomic diversity

**[Thousand Nanopore Genomes Sequencing Consortium](https://millerlaboratory.com/1000G-ONT.html)**

*U of Washington, Oxford Nanopore Technologies, UC Santa Cruz, CZI + ~100 global researchers*

- Understand human genome structural variation patterns, identify variation in difficult-to-map regions of the genome, and study epigenomic patterns across populations.

- Use Shasta to assemble 500 human genomes from across the globe.

## Collaboration

If you are interested in exploring a collaboration with the Shasta team, please contact ssimmonds@chanzuckerberg.com
