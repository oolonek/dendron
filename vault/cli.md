---
id: 9d275a55-3465-45f7-91b4-ff2ba5435ee2
title: CLI
desc: ''
updated: 1621002699407
created: 1611130406336
stub: false
---

# add batch extensions to files

for f in *; do mv "$f" "$f.txt"; done


# lists one file per line

ls -1a


# list files and their path

ls -d -1 "$PWD/"*.*

see https://stackoverflow.com/a/3572628

# find files and order by date 

find ~/ -type f -name "*.key" 2> /dev/null | xargs -0 ls -tl


# check stockage via terminal

df -h

du -h /my/folder

