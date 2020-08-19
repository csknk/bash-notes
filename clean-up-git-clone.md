# Clean up After Accidental Git Clone

If you manage to clone a repo into an unsuitable directory, it can be difficult to clean up since files may become mixed.

```bash
# Make a manifest of git tracked files/directories suitable for deletion
git ls-tree master --name-only > removeList

# Loop over the manifest and delete
for f in $(cat removeList); do rm -rf $f; done
```
