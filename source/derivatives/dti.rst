Diffusion MRI (dMRI)
====================

TractoFlow pipeline is developed by the Sherbrooke Connectivity Imaging Lab (SCIL) in order to process diffusion MRI dataset from the raw data to the tractography.
The pipeline is based on Nextflow and Singularity. The goal with this pipeline is to be fast and reproducible.

Use TractoFlow in published works should be accompanied by the following citation:

    Theaud, G., Houde, J.-C., Boré, A., Rheault, F., Morency, F., Descoteaux, M.,TractoFlow: A robust, efficient and reproducible diffusion MRI pipeline leveraging Nextflow & Singularity, NeuroImage, https://doi.org/10.1016/j.neuroimage.2020.116889.

.. image:: ../imgs/tractoflow.png
    :width: 300
    :align: right
    :alt: Tractoflow image

TractoFlow pipeline
:::::::::::::::::::

TractoFlow pipeline consist of 23 different steps : 14 steps for the diffusion weighted image (DWI) processing and 8 steps for the T1 weighted image processing.

Input
-----
    * Diffusion weighted image (DWI)
    * b-values
    * b-vectors
    * T1 weighted image
    *  Reverse phase encoding B0 (Optional)

DWI processes
-------------
    * Brain extraction (FSL)
    * Denoising (Mrtrix3)
    * Topup (FSL)
    * Eddy (FSL)
    * N4 bias correction (ANTs)
    * Resample (Dipy)
    * DTI metrics (Dipy)
    * fODF metrics (Dipy)

T1 processes
------------
    * Brain extraction (ANTs)
    * Denoising (Dipy)
    * N4 bias correction (ANTs)
    * Resample (Dipy)
    * Registration (ANTs)
    * Tissue segmentation (FSL)

Tractography
------------
The particle filter tractography is performed. Two types of seeding are available: WM-GM interface or WM mask.