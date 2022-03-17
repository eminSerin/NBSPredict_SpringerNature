# NBSPredict_SpringerNature

This repository contains task-based functional connectome data analyzed in two studies presented in a chapter about "NBS-Predict" (Serin et al., 2021) 
in the book “Methods for analyzing large neuroimaging datasets” (Springer Nature) as well as codes to process the data. 

In the chapter, we showed the application of [NBS-Predict](https://github.com/eminSerin/NBS-Predict) to task-based (i.e., movie-watching) functional connectivity data from the ID1000 dataset from the Amsterdam Open MRI Collection (AOMIC) (Snoek et al., 2021) to predict subjects' sex and fluid intelligence. AOMIC can be accessed via https://nilab-uva.github.io/AOMIC.github.io/ without any restrictions. 

The dataset has been initially preprocessed using fmriprep (Esteban et al., 2019). The details of the scanning protocol, scanner, and preprocessing steps are given elsewhere (Snoek et al., 2021). Following the initial preprocessing, we applied the following preprocessing steps:
- Removing tCompCor components which explain 50% of the total variance (Behzadi et al., 2007)
- Removing 24 motion parameters (Friston et al., 1996)
- High-pass filter of 1/128 Hz.
- Spatial smoothing using a Gaussian kernel of 6 mm FWHM.

These further preprocessing steps were performed simultaneously to prevent the reintroduction of artifacts (Lindquist et al., 2019). Following preprocessing, the functional brain images were divided into 268 regions using Shen atlas (Finn et al., 2015; Shen et al., 2013). Pairwise correlations between signals from each brain region were computed to construct a 268x268 correlation matrix (i.e., connectivity matrix) for each subject. We used Nilearn (Abraham et al., 2014) to perform all these steps given above. 

Subjects with an average frame-wise displacement rate above 0.5 mm were excluded from the analyses. This left us 861 subjects in total. 


## Installing

1. Download or clone this repository in a direction of your choice. 

```
git clone --recursive git@github.com:eminSerin/NBSPredict_SpringerNature.git
```

## Dataset

The dataset can be found under the [data](data) directory. The dataset contains: 
- [Connectivity matrices](data/conn_mat)
- [Brain parcellation spreadsheet](data/brain_regions_Shen268.csv), and
- Design matrices for [fluid IQ](data/design_IQ.mat) and [sex](data/design_Sex.mat) prediction analyses.

A detailed description of the specific files involved in the dataset is given in the chapter.
 

## Code

The codes for processing and organizing the functional connectivity data can be found in the [code](code) subdirectory.
 

## References
- Behzadi, Yashar, et al. "A component based noise correction method (CompCor) for BOLD and perfusion based fMRI." Neuroimage 37.1 (2007): 90-101.
- Friston, Karl J., et al. "Movement‐related effects in fMRI time‐series." Magnetic resonance in medicine 35.3 (1996): 346-355.
- Finn, Emily S., et al. "Functional connectome fingerprinting: identifying individuals using patterns of brain connectivity." Nature neuroscience 18.11 (2015): 1664-1671.
- Esteban, Oscar, et al. "fMRIPrep: a robust preprocessing pipeline for functional MRI." Nature methods 16.1 (2019): 111-116.
- Lindquist, Martin A., et al. "Modular preprocessing pipelines can reintroduce artifacts into fMRI data." Human brain mapping 40.8 (2019): 2358-2376.
- Serin, Emin, et al. "NBS-Predict: A prediction-based extension of the network-based statistic." NeuroImage 244 (2021): 118625.
- Shen, Xilin, et al. "Groupwise whole-brain parcellation from resting-state fMRI data for network node identification." Neuroimage 82 (2013): 403-415.
- Snoek, Lukas, et al. "The Amsterdam Open MRI Collection, a set of multimodal MRI datasets for individual difference analyses." Scientific data 8.1 (2021): 1-23.


