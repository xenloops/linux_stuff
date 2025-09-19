# Backing up files

```
rsync -htrXul --info=progress2 <source> <destination>
   -t --times
   -r --recursive
   -X --xattrs
   -u --update
   -h --human-readable output numbers
   -l, --links     copy symlinks as symlinks
   -L              copy symlinks as files
   --delete-delay  find deletions during, delete after
   --specials
```

## Merge two directories, keep newest files

```
rsync -AprRtuvh --dry-run <dir1/> <dir2/>
   -a --archive (preserves attributes) = -rlptgoD
   -r --recursive
   -R --relative
   -u --update (copy only if src newer)
   -v verbose
   -h human readable
   --dry-run
```

cp -au <src/> <dest/>
   -a --archive (preserves attributes)
   -u --update (copy only if newer than dest)

diff -q <dir1> <dir2>
   -q report only differences
   -r recursive
   --brief hide details of content (and speed it up)
