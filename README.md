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

### Step 2: Assembly
- **Date:** 2026-02-24


### Step 1: Validation
- **Date:** 2026-02-24






















