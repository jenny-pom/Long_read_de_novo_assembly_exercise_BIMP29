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
### Step 1: Preperation
- **Date:** 2026-02-24
Make project directory with data, result and script folders.
Initiate github connection by running following commands:
git init # sets up a hidden .git folder
git remote add origin https://github.com/jenny-pom/Long_read_de_novo_assembly_exercise_BIMP29.git
git remote -v # Show me exactly which web address I am connected to.
git add . 
git commit -m "Initial commit of directory structure"
git push -u origin main --force # This sends everything that was included in the add . to GitHub. The --force label was added because I had some problem with a README file that I had created and removed in my directory before running git init
git status # Check that everything worked, shows which files are "Untracked" (in red) or "Staged" (in green)
nano .gitignore # create gitignore and add /Data and *.fastq  so that the big datafile isn't pushed to github
git add .gitignore 
git commit -m "Added gitignore to protect against large data uploads"
git push

### Step 2: Assembly
- **Date:** 2026-02-24


### Step 1: Validation
- **Date:** 2026-02-24




















