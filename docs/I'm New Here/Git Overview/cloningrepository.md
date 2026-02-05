<h1> Cloning a Repository </h1>

<h2> What is Cloning? </h2>

Cloning creates a local copy of a remote repository on your computer. This gives you:
- All project files
- Complete commit history
- All branches
- Connection to the remote repository

<h2> How to Clone a Repository </h2>

Using VS Code:
1. Open VS Code
2. Press Ctrl+Shift+P (Cmd+Shift+P on Mac)
3. Type "Git: Clone" and select it
4. Paste the repository URL from GitHub
5. Choose a folder to save the repository
6. Open the cloned repository

Using Command Line:
```
git clone https://github.com/YourTeam/YourRepo.git
cd YourRepo
```

<h2> After Cloning </h2>

Once cloned:
- Build the project to verify everything works
- Install any necessary vendor dependencies
- Create a new branch for your work
- Never commit directly to main branch
- Always pull latest changes before starting new work
