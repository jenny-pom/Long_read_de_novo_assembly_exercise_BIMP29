# Long-read de novo Assembly of *Saccharomyces cerevisiae*

This project performs a de novo assembly of yeast (HiFi PacBio reads) as part of the BIMP29 course. 
The goal is to assemble the genome and evaluate its completeness using BUSCO.

**Author:** Jenny LN
**Dataset:** SRR13577846 (HiFi PacBio reads)

## Repository Structure
- `Data/`: Raw sequence reads (Read-only, not tracked by Git).
- `scripts/`: Bash scripts for assembly and quality control.
- `results/`: Summary tables and assembly statistics.
- `README.md`: Project documentation and log.

## Process Log

### Step 1: Preparation
- **Date:** 2026-02-24  

First, I created the project directory structure including `Data/`, `results/`, and `scripts/` folders. 

Next, I initiated the GitHub connection and linked the local server to the remote repository:

```bash
git init 
git remote add origin [https://github.com/jenny-pom/Long_read_de_novo_assembly_exercise_BIMP29.git](https://github.com/jenny-pom/Long_read_de_novo_assembly_exercise_BIMP29.git)  
git remote -v # used to verify the connection to the correct GitHub URL
```

Then, I staged the folders and pushed them to the main branch:

```bash
git add .  
git commit -m "Initial commit of directory structure"  
git push -u origin main --force # The --force flag was used to overwrite the existing remote history caused by the initial README conflict.
```
Finally, I checked the repository status and set up the .gitignore to prevent large sequence files from being uploaded.

```bash
git status
nano .gitignore
git add .gitignore  
git commit -m "Added gitignore to protect against large data uploads"  
git push
```
-------------------------------------------
### Step 2: Quality Assessment of Raw Data
- **Date:** 2026-02-24
- Software: FastQC
- Version: FastQC v0.12.1
- Environment: assembly (Conda)
- Input Data: Data/SRR13577846.fastq.gz
Command run: 
```bash
time fastqc -t 10 Data/SRR13577846.fastq.gz -o Results/fastqc/
```
- Time taken: A few seconds
- Notes:
--------------------------------------------
### Step 3: hifiasm
- **Date:** 2026-02-24
- Software: Hifiasm
- Version: 0.25.0-r726
- Environment: assembly (Conda)
- Input Data: Data/SRR13577846.fastq.gz
Command run: 
```bash
time hifiasm -o Results/assembly/hifasm_assembly -t 10 Data/SRR13577846.fastq.gz
```
- Time taken: 19 minutes and 17.5 seconds
- Notes:
  
--------------------------------------------
 I had to turn the .gfa file in to a .fasta file by running:
```bash
awk '/^S/{print ">"$2"\n"$3}' results/assembly/hifasm_assembly.bp.p_ctg.gfa > results/assembly/primary_assembly.fasta
```
--------------------------------------------

### Step 4: Quast (The "Stats" Reporter)
- **Date:** 2026-02-24
- Software: Quast
- Version: QUAST v5.3.0
- Environment: assembly (Conda)
- Input Data: primary_assembly.fasta
Command run: 
```bash
time quast.py Results/assembly/primary_assembly.fasta  -o Results/quast -t 10 --fungus
```
- Time taken: 0m6.331s
- Notes:
--------------------------------------------
### Step 5: BUSCO (The "Biological" Check)
- **Date:** 2026-02-24
- Software: BUSCO
- Version: BUSCO 6.0.0
- Environment: assembly (Conda)
- Input Data: primary_assembly.fasta
Command run:
```bash
time busco -i Results/assembly/primary_assembly.fasta -m genome -l saccharomycetes_odb10 -o results/busco -c 10
```
- Time taken: 1m44.149s
- Notes:
--------------------------------------------
### Step 6: MultiQC 
- **Date:** 2026-02-24
- Software: MultiQC
- Version: multiqc, version 1.33
- Environment: assembly (Conda)
Command run:
```bash
time multiqc Results/ -o Results/multiqc_report
```
- Time taken: 0m5.987s
- Notes:
--------------------------------------------
























