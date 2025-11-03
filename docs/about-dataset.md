# WISCONSIN BREAST CANCER DATA 

The Wisconsin Breast Cancer Dataset represents one of the earliest and most successful integrations of medical expertise, digital image analysis, and machine learning. It remains a benchmark dataset for evaluating classification algorithms in biomedical data science due to its diagnostic relevance, interpretability, and rich morphological feature set. 

## History of the Wisconsin Breast Cancer Data 

The Wisconsin Breast Cancer Data originates from research led by Dr. William H. Wolberg, a professor at the Departments of Surgery and Human Oncology at the University of Wisconsin. The goal was to accurately diagnose breast tumours using Fine Needle Aspiration (FNA) cytology, which is a minimally invasive procedure where cell samples are extracted from breast masses for microscopic examination.

**Diagnosis Phase:** 

Dr. Wolberg collaborated with Prof. O.L. Mangasarian and two of his graduate students, Rudy Setiono and Kristin Bennett, to develop a classifier based on nine visually assessed cytological features derived from FNA samples. 

These features, such as clump thickness, uniformity of cell size and shape, and bare nuclei, capture the morphological characteristics of the cells relevant for distinguishing between benign and malignant tumours. Their early classifier, built using the Multisurface Method (MSM) of pattern separation, achieved a diagnostic accuracy of 97%, forming the foundation of what became the Wisconsin Breast Cancer Data.

**Digital Image Analysis (Xcyt System):** 

In 1990, Nick Street, a professor at the University of Iowa, joined the team to automate the analysis process using digital image processing. A software system called Xcyt was developed, which:
  
- Scans a stained microscope slide containing FNA material. 
- Isolates and segments each nucleus using an interactive computer vision method (“snakes”). 
- Computes ten quantitative features per nucleus that describe the size, shape, and texture.
- Aggregates these as the mean, standard error, and extreme values across all nuclei, producing 30 numeric features per sample.

Using a training set of 569 samples, the researchers built a linear classifier that separated benign from malignant tumours with high accuracy and provided probabilistic diagnostic confidence to clinicians.

**Prognosis Phase:** 

Beyond diagnosis, the research extended to prognosis, that is, predicting long-term disease outcomes such as recurrence.

A method called Recurrence Surface Approximation (RSA) was introduced to estimate the probability of disease-free survival over time based on cytological features.

Results suggested that detailed cellular information derived from FNA samples could outperform traditional prognostic factors such as tumour size and lymph node status, highlighting the clinical importance of cytological image analysis.

## More About the Features of the Dataset  

There are 11 features in this dataset. They are explained in detail below. 

1. **Sample Code Number:** It is the ID number of each sample.
   
2. **Clump Thickness:** 
   - It refers to the density and compactness of a mass of cells. 
   - Cancer cells often travel in clumps to resist hostile environments, while normal cells tend to form thin, monolayer sheets. 
   - High clump thickness can indicate malignancy.
   
3. **Uniformity of Cell Size:**
   - It refers to the consistency in the size of cells within a sample. 
   - Normal cells are generally uniform in size. Cancer cells, however, vary widely in size. Hence, a lack of uniformity in cell size is a key indicator of cancerous cells. 

4. **Uniformity of Cell Shape:**
   - It refers to the consistency in the shape of cells within a sample. 
   - Normal cells tend to have a consistent shape. Cancer cells often have irregular shapes, so
variations in cell shape can signal cancer. 

5. **Marginal Adhesion:** 
   - It refers to the tendency of cells to stick to each other. 
   - Normal cells exhibit strong adhesion to one another, whereas cancer cells lose this ability, which allows them to detach and spread. Reduced marginal adhesion is a marker of cancer.

6. **Single Epithelial Cell Size:** 
   - It refers to the size of individual epithelial cells. It is related to uniformity. 
   - Enlarged epithelial cells can indicate malignancy.
   
7. **Bare Nuclei:** 
   - The term is used for those nuclei that are not surrounded by cytoplasm. 
   - Bare nuclei are typically seen in benign tumours. Their presence can help differentiate between
benign and malignant tumours.

8. **Bland Chromatin:** 
   - This feature describes the texture and appearance of the chromatin (material within the nucleus) in cells. 
   - In benign cells, chromatin has a uniform texture. In cancer cells, chromatin is usually coarser and irregular, helping to identify malignancy. 

9. **Normal Nucleoli:** 
    - They are small structures within the nucleus involved in the production of ribosomes. 
    - In normal cells, nucleoli are typically small and sometimes not visible. 
    - In cancer cells, nucleoli become larger and more prominent, often increasing in number, which is a sign of malignancy. 
   
10. **Mitoses:** 
    - It is the process of cell division. 
    - The rate of mitosis can indicate how quickly cells are proliferating. 
    - A high number of mitoses suggests rapid cell division, which is characteristic of cancerous growth.
   
11. **Class:** 
    - A value of 2 indicates the sample is benign. 
    - A value of 4 indicates the sample is malignant.
