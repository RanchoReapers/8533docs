<h1> Downloading Code </h1>

<h2> Downloading vs Cloning </h2>

There are two ways to get code from GitHub:
- **Downloading**: Gets just the files (no Git history)
- **Cloning**: Gets files AND complete version control

For FRC development, always clone rather than download so you can:
- Commit your changes
- Push to GitHub
- Pull updates from teammates
- Use branches effectively

<h2> When to Download Instead of Clone </h2>

Only download (not clone) when:
- You want to view code without contributing
- Getting example code to reference
- Downloading release packages
- Getting files for a completely different project

<h2> Downloading from GitHub </h2>

If you must download:
1. Navigate to the repository on GitHub
2. Click the green "Code" button
3. Select "Download ZIP"
4. Extract the ZIP file
5. Note: Downloaded code is NOT a Git repository

<h2> Converting a Download to a Repository </h2>

If you downloaded code but need Git features:
1. Create a new repository on GitHub
2. Initialize Git in the downloaded folder: `git init`
3. Add the remote: `git remote add origin <URL>`
4. Stage and commit all files
5. Push to GitHub
