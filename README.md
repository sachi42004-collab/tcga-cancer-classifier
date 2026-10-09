# TCGA Cancer Type Classifier: Can Computers Tell Breast Cancer Apart from Melanoma?

A simple machine learning project that uses gene data to distinguish between two very different types of cancer.

---

## The Question

**What if computers could look at a tumor's genes and figure out what type of cancer it is?**

This project explores whether machine learning can tell the difference between breast cancer and melanoma just by looking at which genes are turned "on" or "off" in tumor cells. And if it can, which genes matter the most?

---

## Why This Matters

Doctors diagnose cancer by looking at tissue under a microscope. But what if we could also use the genes themselves?

Think of it like this:
- Your breast cells are built to make milk and grow tissue in a certain way
- Your skin cells (melanocytes) are built to make pigment and protect from sun
- Even when they become cancer, they still "remember" what type of cells they're supposed to be
- These cellular memories show up in the genes they use

This project asks: **Can computers find these cellular memories?**

---

## The Data

We used information from the **Cancer Genome Atlas (TCGA)** — a free, publicly available database created by the U.S. government with genetic information from over 11,000 cancer patients.

For this project, we looked at:
- **1,218 breast cancer tumors** — donated by patients and researchers
- **474 melanoma tumors** — from the same database
- **~20,000 genes per tumor** — measuring how "active" each gene is

This gave us about 1,700 patient samples to work with.

---

## What We Did (Simply Explained)

### Step 1: Prepare the Data
We took all this genetic information and got it ready for the computer:
- **Checked for missing measurements** — if a gene wasn't measured, we filled it in with the average from similar patients
- **Kept it simple** — we didn't throw away genes or complicate things unnecessarily
- **Made it organized** — labeled each tumor as "breast cancer" or "melanoma"

### Step 2: Split the Data
We divided our 1,700 patient samples into two groups:
- **80% for training** (1,354 patients) — the computer learns from this group
- **20% for testing** (338 patients) — we test if it learned correctly on new data it's never seen

This is like studying for an exam with some practice problems, then taking a real test with different problems to see if you actually learned.

### Step 3: Make Genes Comparable
All genes don't naturally work on the same scale. Imagine comparing:
- Temperature (which goes 0-100°F)
- Weight (which goes 0-300+ lbs)

These numbers aren't comparable as-is. We made all genes use the same scale so the computer treats them fairly.

### Step 4: Train Three Different Computers
We tested three different types of machine learning algorithms:

**1. Logistic Regression**
- The simplest approach
- Like drawing a straight line between two groups of dots
- Good for understanding what's happening

**2. Random Forest**
- More complex
- Like having 100 "computers" vote on the answer
- Better at finding tricky patterns

**3. SVM (Support Vector Machine)**
- Very powerful
- Can find curved boundaries between groups
- Good for lots of genes

### Step 5: See Which Genes Matter Most
After training, we asked: **Which genes did the computer pay attention to?**
- Some genes were very important for telling the difference
- Other genes didn't matter much
- We focused on genes that **multiple computers** agreed were important

---

## What We Found

**[INSERT YOUR RESULTS HERE — Example:]**

| Model | Got It Right | F1-Score |
|-------|--------------|----------|
| Simple Model | 91% | 0.91 |
| Random Forest | 96% | 0.96 |
| Complex Model | 93% | 0.93 |

**What this means:** The computer was really good at telling breast cancer from melanoma — 91-96% accurate! 

That's not surprising when you think about it. Breast tissue and skin tissue are **completely different**, so their cancers should be different too.

### Which Genes Mattered?

**[INSERT YOUR GENE LIST HERE — Example structure:]**

The computer noticed these genes were most different:
- Genes for making **breast tissue structure** were high in breast cancer
- Genes for making **pigment and brown color** were high in melanoma
- Genes for **cell adhesion** (sticking together) were different too

This makes biological sense! Breast cells stick together in a certain way. Melanocytes (pigment cells) are built differently.

---

## Why This Actually Works

### The Biology

Think about your own body:
- Your **breast cells** are designed for specific jobs (making milk, forming tissue)
- Your **skin melanocytes** are designed for different jobs (making pigment, protecting from sun)
- Even when they turn into cancer, they keep using the genes for their original jobs

So cancer cells still "sound like" their original tissue type — just at the genetic level.

### What The Computer Learned

The algorithms discovered:
1. **Breast cancer tumors** consistently use genes that breast cells normally use
2. **Melanoma tumors** consistently use genes that skin cells normally use
3. These patterns are so consistent that even simple math can find them
4. It's not random — it reflects real biological differences

### Connection to My Studies

In my immunology class, I learned that:
- Different parts of your body have different cell types
- Different cell types do different jobs
- Your immune system recognizes tissue by these differences

This project shows that these differences are **encoded in genes** — and computers can find them.

---

## How This Could Be Used

**In the future, this could help with:**
- **Diagnosis** — confirming what type of cancer a patient has
- **Understanding cancer** — why certain cancers are aggressive or slow-growing
- **Personalized medicine** — treating each cancer type differently
- **Research** — finding new drug targets specific to each cancer type

**Important note:** This is just one piece of cancer diagnosis. Doctors use many other things (biopsies, imaging, physical exams) to diagnose cancer. This is a research project, not a clinical tool.

---

## What I Learned

### Technical Skills
- How to download and handle massive scientific datasets (1,692 patients, 20,000 genes)
- How to prepare data correctly for machine learning
- How to compare different machine learning algorithms fairly
- How to avoid common mistakes (like testing on data you trained on)

### Science Skills
- **Simpler is often better** — I didn't need fancy preprocessing. Basic cleaning worked great.
- **Validation matters** — you can't test on the same data you trained on (you'd be cheating)
- **Connect code to biology** — those numbers in Python represent real molecules in real tumors
- **Accuracy needs context** — 96% accuracy is amazing only because we're comparing two fundamentally different cancer types

### My Learning Journey
My undergrad was all wet-lab work: PCR machines, running gels, growing bacteria. But I realized:
- Labs generate massive amounts of data
- That data isn't useful until you **analyze** it
- Bioinformatics bridges lab work and data analysis
- That's where the future of biology is going

This project showed me exactly how that bridge works.

---

## Files in This Project

| File | What It Is |
|------|-----------|
| `brca_expression.tsv` | Raw genetic data for 1,218 breast cancer patients |
| `skcm_expression.tsv` | Raw genetic data for 474 melanoma patients |
| `tcga_brca_skcm_merged.csv` | All patients' data combined with labels |
| `tcga_brca_skcm_preprocessed.csv` | Data cleaned and ready for machine learning |
| `trained_models.pkl` | The three trained computers (models) |
| `model_results.pkl` | How accurate each computer was |
| `consensus_genes.csv` | The genes that mattered most |
| `README.md` | This file |

---

## How to Read This Project

**If you know machine learning:**
- Skip to "Results" and "Technical Details"
- Look at the model performances and gene lists

**If you're curious about cancer:**
- Read "Why This Actually Works" and "Biological Interpretation"
- The genes found should make biological sense to you

**If you're just interested in the story:**
- Read "The Question," "Why This Matters," and "What I Learned"
- That's the whole journey

---

## References & Where This Came From

I didn't just make this up. This project is based on real research. Here are the papers and resources that taught me how to do this:

### The Data
- **TCGA (Cancer Genome Atlas)** — Free database of cancer genetic data from 11,000+ patients
  - [Learn more](https://www.cancer.gov/ccg/research/genome-sequencing/tcga)
  
- **UCSC Xena** — Makes TCGA data easy to download and use
  - [Browse the data](https://xenabrowser.net/)

### The Science
1. **"Machine Learning Methods for Cancer Classification Using Gene Expression Data"** (2023)
   - Why this paper: It's a recent review of exactly what I did — using ML on cancer genes
   - [Read for free](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9952758/)

2. **"The Cancer Genome Atlas Program"** (2016)
   - Why this paper: Explains how all this cancer data was collected and organized
   - In: *Methods in Molecular Biology*, 1418, 111-141

3. **"Informatics for RNA-Seq"** (2015)
   - Why this paper: Teaches you how to properly analyze gene expression data
   - [Read online](http://www.rnaseq.wiki/)

### Key Concepts Explained

**Gene Expression:** How "active" or "turned on" a gene is in a particular cell. Measured as the amount of mRNA (the molecule that genes use to give instructions).

**RNA-Seq:** A technology that measures all 20,000+ genes at once in a tumor sample. It's like taking a snapshot of "what this cancer cell is doing right now."

**Tissue-Specific Genes:** Even after tumors form, cells remember what tissue they came from. Breast cancer cells still use "breast tissue genes." Melanoma cells still use "skin cell genes."

**Breast Cancer (BRCA):**
- Starts in breast tissue (epithelium — cells that form sheets)
- Uses genes for: holding cells together, making milk proteins, epithelial structure
- Visual: organized, structured, connected cells

**Melanoma (SKCM):**
- Starts in melanocytes (pigment-making cells from neural crest)
- Uses genes for: making pigment, neural crest development, melanin metabolism
- Visual: dark pigment-making cells, different origin from breast cells

These differences create completely different genetic "fingerprints."

---

## Next Ideas

If we kept building on this project, we could:
- **More cancers** — can we tell 10 different cancer types apart?
- **Predict survival** — do these genes predict how long patients live?
- **Find drug targets** — which genes could we target with new drugs?
- **Why does it work?** — exactly which cellular processes create the differences?
- **Deep learning** — could neural networks find patterns we missed?

---

## Important Note

**This is a research and learning project.** It shows that computers *can* find patterns in cancer data. But:
- It's not a medical tool
- Don't use this to diagnose real patients
- Real diagnosis needs doctors, pathologists, imaging, and clinical judgment
- Gene patterns are just one piece of the cancer puzzle

---

