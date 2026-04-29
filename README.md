# TUDelft-LIVI-Downstream
Automated downstream analysis pipeline for correlating LIVI donor latent factors with RA clinical subtypes (CTAPs) and mapping them to druggable pathways. 

---

## 🎯 Project Goal
The goal of this project is to bridge the gap between the latent representation of gene expression in single cells, produced by deep-learning models, and clinically valuable insights. By analyzing the latent space of the LIVI Variational Auto Encoder (VAE), the aim is to identify the driving genes behind clinical heterogeneity within RA patients.
Specifically this project is meant to aid research in answering the following research questions: To what extent do RNA-derived LIVI
latent factors capture clinically relevant RA inflammatory subtypes (heterogeneity) and can they
be used to identify druggable pathways? To do so, the main question can be divided in three subquestions:
Subquestions
1. Do the donor-specific latent factors produced by LIVI show statistically significant correlation
with the six inflammatory subtypes of RA defined by Zhang et al?
2. Do the most significant genes derived from the decoder weights align with the known cell-type
structure of the predicted CTAPs?
3. Do these top driving genes map to druggable inflammatory pathways?

---

## 🔨 Implementation Roadmap

### 1. Find correlations between latent factors and CTAPs
- [ ] **Integrate Data**: Merge donor embeddings ('D') with clinical metadata (from Zhang et al.).
- [ ] **Distribution validation**: Run **(TBD) but probably Shapiro-Wilk \ Levene ** to identify CTAP-specific latent factors.
- [ ] **Variance Analysis**: Run **(TBD) but probably ANOVA \ Kruskal-Wallis ** to identify CTAP-specific latent factors.
- [ ] **P-value Correction**: Run **(TBD) but probably Tukey's HSD \ Dunn's** corrections to ensure valid p-values.

### 2. Map significant factors to biological pathways
- [ ] **Decode Significant Factors**: Extract gene weights from linear decoder ('W_DxC') using a $100 \times \text{IQR}$ threshold.
- [ ] **Pathological Validation**: Perform GSEA (using gseapy library) to find existing biological pathways corresponding to the extracted genes.
- [ ] **Drug Discovery**: Automatically query pharmaceutical database. **(TBD) but probably Open Targets GraphQL API** to identify potential drugs matching the found pathways.

---

## 🖥️ Tech Stack
- **Languages:** Python 3.13.12
- **Libraries:** pandas, scanpy, scipy, statsmodels, gseapy **(most likely)**
- **APIs:** Open Targets Platform (GraphQL) **(most likely)**
- **Environment:** Delft AI Cluster (DAIC)

  ---
  
## 🎓 Background & Context
This project is part of a Bachelor of Science Thesis at **Delft University of Technology**. It uses the LIVI model, a Variational Auto Encoder (VAE) originally designed to identify trans-eqtl effects within donors using the OneK1K dataset.
