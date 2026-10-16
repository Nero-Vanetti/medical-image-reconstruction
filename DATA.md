# Local data setup

Datasets are separate from the repository. The notebooks retain saved figures, so their results can be explored without downloading the input data.

| File | Place beside | Required variables |
| :--- | :--- | :--- |
| `CTdata.mat` | `ct/ct_reconstruction.ipynb` | `g`, `g2`, `g3` |
| `MRIdata.mat` | `mri/mri_reconstruction.ipynb` | `kspace_full`, `kspace_coils`, `kspace_subsampled`, `coil_sensitivities`, `nifti_info` |
| `PETdata.mat` | `pet/pet_reconstruction.ipynb` | `G`, `G_noisy` |

Use the course-provided files if you already have authorized access. This repository does not provide a public dataset download or imply permission to redistribute course material. If you do not have the files, you can still read the notebooks and view their saved results.

The `.gitignore` excludes `.mat` inputs, `.npy` intermediates, NIfTI volumes, notebook checkpoints and local virtual environments. The MRI input is approximately 293 MiB and is intentionally kept out of the Git upload package.
