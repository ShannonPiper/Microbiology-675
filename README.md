# Microbiology-675

# Intro 1/22/19
* CPU executes commands
* Memory/RAM is short term storage for programs being run (not permanent)
* Disk space is long term storage (permanent)
* "High speed" CPU is not really the limitation of computers
  * limitation is how fast information can be given to the CPU, determined by the frontside bus through which information from the  northbridge memory (from RAM) is channeled to the CPU.

## Language:
* We think of numbers to the base 10, computers use base 2.
* Base 2 means something is either on or off (1 or 0).

## Windows, Mac, Unix/Linux
* For Windows, the kernel is stacked with the operating system above it and the program is submitted above that. Kernel is where everything germinates/runs from. Doesn't allow users and programs to access the kernel directly (which was thought that it would be harder to hack/break those computers).
* For Unix/Linux, the kernel is accessed by programs directly. The operating system (O/S) is next to it, not stacked on top.
* Mac moved towards the way Unix/Linux does things.


# Introduction to Command Line 1/24/19
* Root access is access to the kernel
 * Do not need root access to install run/programs, just need administrative access
* Basic command line
 * Modify the behavior of `ls` and other commands with flags.
  * `-lap` : lists everything in directory, including hidden files.
  * `-l` : long list format
  * `-a` : shows hidden files
* My home Windows partition when opening Ubuntu can be accessed by:
 1. `cd ..` and `cd ..` again
 2. `cd mnt` then `cd c` then `cd Users` then `cd Shannon`
 3. Then I can access all of my Windows files.
  

# 1/29/19 Next Generation Sequencing and Sequence File Formats
## The Sanger Method:
* Capitalize on dideoxynucleotide triphosphates (ddNTPs)
* Add different color fluorescences to different bases (A, T, C, or G) and run on sequencing gel.
* Stop replication in its tracks and add dye to bases. Still use same technique, more efficiently.

## Next-generation sequencing
* Sanger sequencing is slow and expensive.
* Guy wanted to solve his daughters genetic problem, 454 Pyrosequencing
* 454 Pyrosequencing
  * Library prep using A and B primers to break into smaller fragments for sequencing 
  * Emulsion PCR (emPCR)
   * Attach bead to each fragment, each bead/fragment ends up in one oil bubble
   * Each individual oil droplet ends up in a well
   * Add A, C, T, and Gs to each well.
   * Incorporate luciferin bound dNTPs, each with different color. When incorporate, a flash of light is emitted.
   * A camera notes the lights emitted.
   * Produce the same kind of results as Sanger sequencing. A flowgram shows you which bases were present and if the bases existed in runs.
   * Stops being done for the most part once Illumina sequecing arose
* Illumina Sequencing
 * Use sequencing primers on dsDNA separated into ssDNA
 * An Illumina High-Seq 2000 can produce over 15 Gbp in a single lane (~100 million reads at 150 bp)
 * Only $4,000 per run, takes longer
* Pac Bio Sequencing
 * Invoking polymerase in real time, meaning dependent on half-life of polymerase and generates very long reads
 * High error rate (~12%)
 * Often combine Pac BIo with Illumina to get accuracy of Illumina with long sequences from Pac Bio (good for assemblies)

## FASTA format
* Was originally a program that performed sequence searches of small DNA sequences within a database
* Was replaced with BLAST
* File format used in FASTA now adopted as the sequence data format.
* Anatomy of a FASTA file
 * First line is a record indicator
 * > indicates the beginning of a record.
 * Followed by a geninfo identification number (gi), then an accession number for genbank
 * Followed by a description of the the gene/protein (end of definition line); no limit to how long definition line can be.
 * Followed by the actual sequence
* For eukaryotes:
 * There are exons and introns that must be dealt with.
 * After the gi number, there are listings of base pairs which represent/reference exons in the gene. The sequence stitches together all of the exons if it is representing the mature gene.
* File format extensions:
    * NCBI:
        * Something.faa = fasta amino acid
        * Something.fna = fasta nucleotide
* GenBank/DDBJ Header Anatomy:
 * See slides
