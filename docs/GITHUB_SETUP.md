# Publish this project on GitHub

Suggested repository name: **medical-image-reconstruction**

Suggested description:

> Python coursework in CT, MRI and PET image reconstruction: back-projection, Fourier reconstruction, SENSE and MLEM. Chalmers EEN180.

Suggested topics: `medical-imaging`, `image-reconstruction`, `computed-tomography`, `mri`, `pet`, `python`, `jupyter-notebook`, `biomedical-engineering`.

## Browser upload

1. Extract `medical-image-reconstruction.zip` on your computer.
2. Sign in as [Nero-Vanetti](https://github.com/Nero-Vanetti) and [create a repository](https://github.com/new) named `medical-image-reconstruction`.
3. Choose the intended visibility. Leave the generated README, `.gitignore` and licence options unselected because the package already contains its documentation and ignore rules.
4. On the new repository page, choose the link to upload an existing file. For an existing repository, use **Add file → Upload files**.
5. Upload the **contents** of the extracted `medical-image-reconstruction` folder, keeping the subfolders intact. `README.md` should sit at the repository root. Do not upload the ZIP itself or the outer enclosing folder.
6. Use the commit message `Add CT, MRI and PET reconstruction portfolio` and commit the upload.
7. Check that the homepage displays the README and its figures. Add the description and topics in the repository's About section.

All files in this package are below GitHub's browser-upload limit. Dataset files are not included. If `.gitignore` is hidden by your file manager, make sure it is uploaded too.

Official instructions: [Adding a file to a repository](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository).

## Git alternative

After creating an empty repository, run these commands from inside the extracted project folder:

```bash
git init
git branch -M main
git add .
git commit -m "Add CT, MRI and PET reconstruction portfolio"
git remote add origin https://github.com/Nero-Vanetti/medical-image-reconstruction.git
git push -u origin main
```

The commands assume a new local checkout and an empty remote repository. GitHub authentication is handled by your local Git setup.

## Attribution

The README already states that all code was developed jointly in a pair. The collaborator's name can be added to `CREDITS.md`, the project READMEs and notebook introductions when available. Course material and datasets have separate provenance; this package does not assign them an open-source licence.
