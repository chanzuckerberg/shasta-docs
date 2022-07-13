# FAQ

## Do I need to preprocess my reads?

No. Shasta accepts unprocessed reads as input in .fasta or .fastq formats. Compressed files are not supported, so make sure you decompress reads before running Shasta.

Any reads shorter than the Reads.minReadLength (default 10000) containing bases with repeat counts >255 are automatically discarded. You can adjust the minimum read length in the assembly using the Reads.minReadLength.

## Does it matter what version of Guppy I used to basecall my reads?

Yes. For optimal results, please basecall your ONT reads with the latest version of Guppy (5 or 6) using the super accuracy mode. If your reads are Guppy 4 or earlier, it is worth re-basecalling them before running an assembly.

## Can I run Shasta using Docker?

Yes. The documentation can be found in the [Shasta man pages](https://chanzuckerberg.github.io/shasta/Docker.html){:target="_blank"}

## What is the minimum read coverage required for standard ONT reads?

For standard ONT reads, Shasta performs well with at least 30x coverage of reads ≥10Kb. Optimal coverage is 50-80x of reads ≥10Kb.

You can adjust the coverage by specifying the desired value for total coverage, in bases with the command --Reads.desiredCoverage. For example, to adjust the desired coverage for a 1 Gb genome to 60x, use --Reads.desiredCoverage 60G.

## What is the minimum read coverage required for ultra-long ONT reads?

The optimal coverage for ultra-long (UL) reads is 60-80x of reads N50 ≥ 50Kb.

## How much memory do I need for my genome?

Shasta works on a single large machine and operates in memory.

Memory requirements are roughly proportional to genome size and coverage and are around 4-6 bytes per input base. For a human-size genome (~3 Gb) at 60x, this works out to ~1 TB of memory.

Machines with 1-24 TB of memory are available at reasonable prices on cloud computing platforms (e.g., AWS EC2 instances). For all assemblies requiring up to 1 TB, you should use ARM x2gd instance types. These instances are available at ~$3/hour as on-demand instances. They complete a human assembly at coverage 60x in ~5 hours, at the cost of ~$15 per assembly.

See our [documentation](https://chanzuckerberg.github.io/shasta/Running.html#LowMemory){:target="_blank"} for more detailed information on memory requirements, memory modes and running Shasta with less than optimal memory (i.e., for very small genomes).

## How do I choose a config?

As a starting point, please use the latest assembly configuration corresponding to the length of reads you have and the type of assembly you want to run. For example, if you have standard ONT reads and want to run a haploid assembly, please use Nanopore-May2022. If you're going to run a haploid assembly with ultra-long reads, please use Nanopore-UL-May2022. For more detail please see the [documentation](https://chanzuckerberg.github.io/shasta/Configurations.html){:target="_blank"}.

## Are diploid phased genome assemblies supported?

Yes. Shasta supports resolving haplotypes of diploid genomes. Please run phased diploid assemblies using the appropriate config. For standard read lengths use Nanopore-Phased-May2022 and for ultra-long read lengths use Nanopore-UL-Phased-May2022. In humans, we get the best assemblies (~90% phased diploid) from ONT ultra-long reads with 60-80x coverage and a read N50 of >50Kb. However, other genomes with much higher rates heterozygosity phase well with lower coverage (45x) and standard read lengths.

## My assembly size/contiguity is not what I expected; what parameters can I tweak?

If there is a reference for your species or you have an estimate of the genome size from flow cytometry or karyotyping, then the size of your Shasta assembly should be close to the estimated size. Although, we usually find that Shasta assemblies are slightly smaller than the estimated size. You can try tweaking the read length cutoff --Reads.minReadLength. The default is 10000 for standard ONT reads. If you have low coverage (i.e., less than 60x), you could lower the --Reads.minReadLength (in 2,500-5,000 intervals) increases the amount of coverage used in the assembly and potentially increases the assembly size. If you have reads with 60-80x coverage, you can try increasing the --Reads.minReadLength (in 2,500-5,000 intervals) to remove smaller reads from the assembly and potentially increase the contiguity.

If the above recipe does produce the desired result we recommend you, 1) increase the number of MinHash iterations, for example to 100, 2) set the read graph creation method to 0 (no adaptivity in selecting alignment criteria), 3. experiment with alignment criteria, starting with the values chosen in the out of the box assembly (they are in the assembly log). Generally one needs to increase both minAlignedMarkerCount and minAlignedFraction.

## What polisher do you recommend?

For human genomes, we recommend [Pepper-Margin-DeepVariant](https://github.com/kishwarshafin/pepper/tree/refs/tags/r0.8){:target="_blank"}. For non-humans, we have had good results using one round of the [Flye polisher](https://github.com/fenderglass/Flye/blob/flye/docs/USAGE.md#running-only-flye-polisher){:target="_blank"}, but results may vary.
