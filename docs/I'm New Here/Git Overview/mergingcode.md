<h1> Resolving Merge Conflicts </h1>

<h2> What is a Merge Conflict? </h2>

A merge conflict occurs when Git cannot automatically combine changes from different branches because the same lines of code were modified differently. This commonly happens when:
- Multiple people edit the same file
- Changes are made to a file while it's being edited elsewhere
- A branch hasn't been updated before merging

<h2> Identifying Merge Conflicts </h2>

Git marks conflicts in the file with special markers:
```
<<<<<<< HEAD
Your changes
=======
Incoming changes from other branch
>>>>>>> branch-name
```

The section between `<<<<<<< HEAD` and `=======` is your version.
The section between `=======` and `>>>>>>> branch-name` is the incoming version.

<h2> Resolving Conflicts </h2>

To resolve a merge conflict:
1. Open the conflicted file in VS Code
2. Review both versions of the code
3. Decide which changes to keep (or combine both)
4. Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
5. Test that the code works correctly
6. Stage the resolved file
7. Complete the merge with a commit

<h2> Preventing Conflicts </h2>

Reduce conflicts by:
- Pulling latest changes before starting work
- Making small, focused commits
- Communicating with teammates about what you're working on
- Working on different files when possible
- Merging frequently to keep branches up to date
