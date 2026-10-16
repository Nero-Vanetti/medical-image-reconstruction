# Validation record

Validation performed on 15 October 2026 against the portfolio copies and supplied datasets.

| Project | Check | Result |
| :--- | :--- | :--- |
| CT | All 17 code cells, executed in order in a fresh namespace with CTdata.mat | Passed; final ramp reconstruction 632 × 632, all values finite |
| MRI | All 15 code cells, executed in order in a fresh namespace with MRIdata.mat | Passed; full SENSE output 192 × 129 × 192, all values finite |
| PET | Small synthetic forward model, least-squares reconstruction and 12 MLEM iterations | Passed; finite nonnegative MLEM estimates and decreased projection residual |
| PET | FBP on one slice of the supplied noise-free data | Passed; 87 × 87 × 1 output, all values finite |
| All | Notebook schema validation | Passed |

The execution checks used Python scripts with a noninteractive Matplotlib backend. The single `%matplotlib inline` command in CT was omitted for script execution. This was not a Jupyter browser-session test. Historical outputs were preserved rather than replaced by validation-run outputs. For GitHub upload, figures were externalized into linked assets; three large CT plots use high-quality JPEG display copies.

The full PET notebook, dense full-size matrix construction and full-size least-squares solves were **not** rerun. The small PET system matrix had shape 96 × 64. Its least-squares relative projection residual was 5.32e-08. Over 12 MLEM iterations, the squared projection residual decreased from 136.006 to 0.06844.

## Environment used for execution

- Python: 3.12.14
- NumPy: 2.5.4
- SciPy: 1.18.1
- Matplotlib: 3.10.8
- NiBabel: 5.4.2
- scikit-image: 0.26.0
- nbformat (schema checks): 5.11.1

`requirements.txt` specifies version ranges for local setup, not an exact reproduction lockfile. JupyterLab is provided as the recommended interactive interface; its browser UI was not tested here.

Successful execution confirms that the checked code paths run with these inputs. It does not validate all mathematical conventions, image geometry or written conclusions. See [review notes](REVIEW_NOTES.md).
