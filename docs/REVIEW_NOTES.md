# Review and reproducibility notes

The portfolio preserves the original coursework workflow and saved results. These notes separate documentation and execution checks from scientific validation.

## Changes made for this edition

- For GitHub upload, embedded notebook figures were moved to linked image files under `assets/`; code and numerical text outputs are unchanged. Three large CT figures use high-quality JPEG display copies. The original embedded outputs remain in the downloadable archive provided before publication.

- Added English overview and project READMEs, joint-work attribution, data instructions and dependency declarations.
- Extracted six original result plots into `assets/` without altering their plotted content.
- Added a portfolio introduction to each notebook and standardized filenames.
- Removed an incomplete duplicate `ramp` definition and a standalone `s` expression from the CT notebook. The retained ramp implementation is unchanged. The stray expression could raise `NameError` in a clean session.
- Moved CT's Hamming comparison figure creation before plotting, avoiding a separate empty figure. The numerical calculation is unchanged.
- Removed two CT image references whose source files were not supplied.
- Removed the local Windows user-path prefix from a stored PET warning; retained the warning text.
- Retained assignment text, written answers, existing execution counts and saved result outputs. The README figures are historical outputs, not regenerated validation figures.

## CT

- **Hamming filter convention:** the early `hamming` function uses a nonstandard frequency weighting. A later cell redefines `hamming` as an array-index window and multiplies it directly into unshifted FFT coefficients. These are not a consistent, validated low-pass taper of a ramp filter.
- **CBP labelling:** both functions named `conv_back_project` filter through FFT multiplication, not explicit spatial convolution. The later definition overrides the earlier one. This section does not independently demonstrate spatial-domain convolution back-projection.
- **Random-input experiment:** the CBP comparison uses unseeded random sinogram values and the first N angles, rather than an evenly distributed subset of the original object projections. Rerunning it changes the plot.
- **Sampling:** `linspace(..., dtype=int)` selects integer angle indices with potentially unequal gaps. Some later cells assign a new uniform angle vector instead of retaining each column's original angle.
- **Repeated views:** the `g2` example requesting 360 columns repeats measurements from a 180-view dataset. It does not demonstrate increased acquisition density. The `g3` dataset does contain 360 distinct supplied columns.
- **Coordinate convention:** the nearest-bin back-projector maps using `s + n/2`. This needs reconciliation with the stated detector coordinate range and Python's zero-based indexing before claiming quantitative geometric accuracy.
- **Scaling and comparisons:** display autoscaling and the assignment's normalization are not a quantitative attenuation calibration. Claims of universal superiority of a filter or projection count are not established by these examples.

## MRI

- **NIfTI geometry:** `save_nifti_image` uses an identity affine and separately sets header zooms. It does not propagate the supplied orientation/translation transform; the affine and voxel spacing may therefore be inconsistent. The saved visualization does not validate anatomical orientation.
- **SENSE scope:** the implementation assumes twofold undersampling and the supplied folding/indexing pattern. It is not a general reconstruction for arbitrary acceleration factors or coil geometry.
- **Conditioning:** sensitivity normalization uses an epsilon, and the SENSE solve uses an unregularized least-squares solution. Noise can be amplified in low-sensitivity or poorly conditioned regions.
- **Image quality:** the notebook's visual descriptions do not establish quantitative SNR, diagnostic quality or the precise causes of residual artifacts.

## PET

- **Mismatched reference slices:** `slice_idx` starts at 10 for the noise-free MLEM reconstruction, then changes to 15 in the FBP comparison. Subsequent noisy MLEM uses slice 15, while the stopping comparison still uses the earlier slice-10 reference. The saved optimum of eight iterations is therefore not a validated matched-slice optimum. A corrected comparison must reconstruct the same slice in both cases and regenerate the figures.
- **Reference is not ground truth:** even after matching slices, the reference is a reconstruction of noise-free measurements, not an independent ground-truth activity image.
- **Objective versus diagnostic:** MLEM targets a Poisson likelihood. The code records squared projection residuals; these are a separate diagnostic and do not alone select the best stopping iteration.
- **Direct baseline:** `NAIVE` uses dense least squares. It should not be described as naive/unfiltered back-projection.
- **Model scope:** the forward model accounts for geometry, without attenuation, scatter or detector-efficiency corrections. A saved scikit-image warning reports basis-image values outside the reconstruction circle.
- **Cost:** the full system matrix has 118,530,540 float32 entries (about 452 MiB). Dense least-squares solving needs additional memory. The current notebook saves matrix files but still computes the matrix on a fresh top-to-bottom run.

## Validation

Validation details are recorded in `VALIDATION.md`. Successful execution or a numerical smoke check does not resolve the scientific limitations above.
