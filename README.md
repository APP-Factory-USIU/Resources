# Resources

This repo contains various resources that may be of use to members for various projects.

What to expect:

1. Introduction to GitHub.md - Introduces you to Git and GitHub.
2. SSH Setup.md - For setting up SSH on your machine.
3. SLMS.md - SLMS setup.
4. README.md - This description.

## Workflow Documentation

This repo uses **GitHub Actions** to keep documentations as one format.

### How it works

- If you have word documents, place the files in the `MS-Word` folder.
- On every push, GitHub automatically converts `.docx` to `.md` using [Pandoc].
- Wait for the Action to complete conversion (Check the **Actions** tab for the progress).
- After completion, the `.md` file will appear in the root folder.
- Any images/screenshots in your word documents are extracted into `/media/` and linked in the Markdown.

### Why
- `.docx` can't be viewed from GitHub natively thus require downloading first.
- `.md` files render natively in GitHub, so people can view documents without downloading files.

### Note:
1. Don't edit the `.md` files directly, as they will be overwritten on the next conversion run.
2. Only put .docx files in the MS-Word folder.
3. If the document is already in MarkDown, just put it in the root folder.
