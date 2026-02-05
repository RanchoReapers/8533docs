<h1> Staging vs Committing </h1>

<h2> What is Staging? </h2>

Staging (also called "adding") is the process of selecting which changes you want to include in your next commit. Think of it as preparing a package before shipping it.

The staging area allows you to:
- Review changes before committing
- Group related changes together
- Exclude temporary or unfinished work
- Create clean, focused commits

<h2> What is Committing? </h2>

Committing takes all staged changes and creates a permanent snapshot in your repository's history. Each commit should:
- Have a clear, descriptive message
- Contain related changes (one logical change per commit)
- Be complete and functional (doesn't break the build)
- Follow your team's commit message conventions

<h2> The Workflow </h2>

The typical workflow is:
1. Make changes to files
2. Review what you changed
3. Stage the files you want to commit (git add)
4. Commit the staged changes with a message (git commit)
5. Push commits to GitHub (git push)
