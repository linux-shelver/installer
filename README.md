# installer
Master yuros linux installation


# register library
Add the remote for the subtree repository (optional but recommended):

This step adds a named remote to your repository, making it easier to reference the subtree's source.
```
git remote add <remote-name> <URL to Git repo>
```

Replace <remote-name> with a descriptive name (e.g., library-remote) and <URL to Git repo> with the URL of the repository you want to add as a subtree. Add the subtree.
This command performs the actual integration, pulling the subtree's content into a specified local directory.

```
git subtree add --prefix=<folder-path> <remote-name> <subtree-branch-name> --squash
```
--prefix=<folder-path>: Specifies the local directory within your repository where the subtree's content will reside (e.g., vendor/library).
<remote-name>: The name of the remote you added in the previous step.
<subtree-branch-name>: The branch from the remote repository you want to integrate (e.g., main or master).
--squash: This option is highly recommended as it condenses the entire history of the subtree into a single commit in your main repository, preventing a large influx of commits and keeping your main repository's history cleaner. If you need the full history of the subtree, omit this flag.


```
git remote add library git@github.com:linux-falcone/libmake.git
```

```
git subtree add --prefix=library library main --squash
```

After executing these commands, the contents of the specified branch from the remote repository will be integrated into the designated folder within your main repository. You can then interact with these files as if they were part of your main project, while still retaining the ability to pull updates from the original subtree repository or push changes back to it using git subtree pull and git subtree push commands.
