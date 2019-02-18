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

## 1/31/2019
* Sequence alignment
    * Local alignment: limit number of deletions
        * Good for comparing short sequences to large ones
    * Global alignment: braodest pairing across the board, regardless of insertions and deltions
* A good alignment contains subsequences of absolute identity (short lengths of exact matches)

# BLAST 2/7/2019
* standard format for searches: `blast -query input -db database -out output -evalue le-05`
    * can add argument `-outfmt 6`

# Introduction to Genomes and Genome Assembly 2/7/2019
* What's in a genome? All genetic material within a given organism
* What elements can you obtain form a genome?
    * Entire DNA sequences
    * ORF/ESTs
    * 
* 1995: first paper comes out that characterizes the entire genome of a prokaryote. Before this, people only dealt in genes. After 1995 is considered the genomic era.
* whole-genome shotgun:
    * cut up genome into a lot of random tiny pieces and you sequence all of those pieces. Use computer algorithm to put these pieces together: Assembly
    * The goal is the cover the entire genome using reads that are ontained from the sequencer.
    * The more reads and the larger reads make it easier to cover the entire genome. But there is a trade-off between read-length and coverage.
* Terms:
    * Coverage: the number of times a give bp in a geonome is sequences on average.
        * Also provides confidence in a base call.
        * A complex genome has a coverage of 10-15X; Draft is <8X
* What contributes to assembly difficulties?
    * Read length
    * Coverage
    * Repeat Elements
        * Length helps solve this problem
* Draft vs. complete genomes
    * Complete chromosome: orintation known
    * Multiple contigs: orientation may be known; this is fine for a lot of people to answer specific questions.


# 2/12/2029 Genome Assembly continued
* Genome finishing
    * Fill in the gaps between contigs
    * Very expensive
* Approaches to improve an assembly:
    * mate-paired/paired-end sequencing - a way to determine relative orientation (454 techonology specific, different from paired-end reads from illumina)
    * Used to obtain a Scaffold - a low cverage DNA sequence that can be used to map a while-genome shotgun reads onto.
    * Cut DNA into fragments that are a certain size which can be sequenced by the sequencer, know sequence right next to biotin and can walk from there across gap between biotin sequences to generate small overlapping sequences that fill in a gap.
* Assembly statistics:
    * N50: contig or scaffold N50 is a weighted median statistic such that 50% of the entire assembly is contained in contigs greater than or equal to the median/N50 contig size.
        * Want N50 to be large enough that a contig likely contains a gene within the average reading frame of that organism.
* Assembly:
    * Fragment DNA and sequence
    * Look for overlapping regions in reads
    * Generate map or graph of sequences that match each other. Becomes mathematical question
    * Must compare every read against every other read.
    * Becomes very challenging for short reads
* De Bruijin Graph:
    * Faster approach
    * Break down each sequences into a smaller subset.
    * Computes a K-mer, a subset of K length from the read itself.
    * A graph is constructed from the K-mer subsets
    * Now the somparison is reduced to looking for patterns in the graphs
    * It is less time-consuming to find the total number of "patterns" in a group of patterns than pair-wise comparisons of every read.
    * Once pattern groups are formed, the assembly proceeds in a similar manner as the traditional approach.
* The Celera Assembler
    * An assembler developed specifically for assembly of the human genome
    * Considered the premier assembler of its time.
* Anatomy of WGS assembly
    * Allow mismatches to fill in gaps in contigs.
* Scaffold:
    Typically generate from mate-paired sequences
* Celera Assembly Pipeline
    1. Trim and screen: 
        * Reads are quality-trimmed.
        * Contaminant and vector sequences are removed. Also avoid low-quality sequences.
        * Make a note of reads with repeats.
        * gatekeeper program to vet inputs/assign IDs
    2. Overlapper:
        * Finds all of overlaps > 40bp allowing 6% mismatch
    3. Unitiger: assemble comtigs
        * Compute all overlap consistend sub-assemblies. Unitigs (Uniquely Assembled Contig).
    4. Scaffolder: layer Unitigs onto scaffold
    5. Repeat Rez I, II:
        * Fill repeat gaps with doubly anchored positive unitigs
        * Fill repeat gaps with assembled, singly anchored reads.
* Anatomy of a fastq (Illumina) file
    * Quality scores: the Phred score
        * Phred is a commonly used metric in Sanger to indicate the quality of a base call.
        * Represented as the probability of an incorrect base call.
    * Fastq file similar to fasta file, but it contains information about the quality of the basepair call from the sequencer.
        * Line 1: Always starts with @ and contains run information
        * Line 2: Always starts with # and contains the base calls. Starts with the primer thing
        * Line 3: Always starts with + and contains additional information about the call
        * Line 4: Contains the quality score for each base.
            * Each character on this line represents an ASCII value. Subtract 33 form that number to get a quality score.
            
# Celera Assembler Download 2/14/2019
* Installation process
    * Compile source code
    * Install program -> compiles into binaries that computer recognizes as executables
    * Creates binaries and thus executables in the folder from which they are created.
    * `apt-get` compiles binaries and puts them in folder in root directory (`/bin`)
        * Computer can use exectuables in the bin folder
    * For Celera, we need to make sure we move the binaries into the bin folder, or make celera fold have the same privelages as the `/bin` folder.
    * All of the folders which the computer can automatically run executables are include in the `$PATH`. List of folders that the computer will look through for executables when using command line.
* Tarring a file into a tar ball maintains the hierarchy of the folder you are working with.
