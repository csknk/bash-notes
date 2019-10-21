Symlinks
========

New Symlink
-----------
Create a new symlink (fails if symlink exists already):

```bash
ln -s /path/to/source-file /path/to/symlink-name
```
If you are currently in the directory that will contain the symlink, you don't need `/path/to/symlink-name` - `symlink-name` is enough.

Amend Existing Symlink
----------------------
Use the `-f` option:

```
ln -fs /new/path/to/source-file /path/to/symlink-name
```
