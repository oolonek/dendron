---
id: 1cfa0181-c229-46f5-a545-6e84a1a0c551
title: Biblio
desc: ''
updated: 1609599895179
created: 1609570147699
---

# Bib integration in dendron 

Messing around with pandoc citer and trying to integrate bibliography management in dendron


The markender extension (https://github.com/mjwsteenbergen/markender) is causing conflict with pandoc citer for the autocompletion.
Deactivate Markender



Conflict thrown  [[public.project.tramadol]] 

Error: Command failed: pandoc --from=markdown-raw_tex+tex_math_single_backslash --to=html --katex --filter pandoc-citeproc
Error reading bibliography /Users/pma/Documents/library_formatted.bib (line 60541, column 1):
unexpected end of input
expecting "}", "\\" or "{"
Error running filter pandoc-citeproc:
Filter returned error status 1

Now trying to troubleshoot the file using bibdesk


## Bib file formatting 

Bib file formatting is required to avoid the previous error. This error is somehow misleading because it indicates that the error comes from the end of the file ... and it's not the case, rather a curly brace somewhere which is not closed.

From the automatically sync .bib of Mendeley, make a copy and ctrl+F replace all \{ by \'{ and all all \} by \'}
This should make the trick.


TODO automate with a sed script ? the bib cleaning 

Some sed black magic 

```bash
echo "\{" | sed "s|\\\{|\\\'{|"
````
Double \\ to escape the \\

And repeat 

```bash
echo "\{jhdgjshgjhfsjdhgf\}" | sed "s|\\\{|\\\'{|g; s|\\\}|\\\'}|g;"
````
Now add input and outputs 

```bash
sed "s|\\\{|\\\'{|g; s|\\\}|\\\'}|g" library.bib > library_formatted.bib
```

We'll try to automatize the process using https://stackoverflow.com/a/13807906 fswatch and alternative to inotifywatch on linux https://linux.die.net/man/1/inotifywatch

So here is the small bash script. It will take the command line arg 1 and add the _formatted prefix to it. Could be cleaner and directly extract the filename to accomodate for various type of extension. Not the point here. If any body has an idea, please contribute ! :point_down: 


```bash
#!/bin/bash
sed "s|\\\{|\\\'{|g; s|\\\}|\\\'}|g" "$1" > "${1%.bib}_formatted.bib"
```

```bash
#!/bin/bash

# fullfilename="$(basename $1)"
# extension="${fullfilename##*.}"
# filename="${fullfilename%.*}"

# echo $fullfilename
# echo $extension
# echo $filename

#echo "File added: " "$(basename $1)" "$(basename $1)"
sed "s|\\\{|\\\'{|g; s|\\\}|\\\'}|g" "$1" > "./formatted_bib/${filename}_formatted.bib"

````




fswatch has been somehow a nightmare to understand ...

to trouble shoot use the follwoing line to be sure of what exactly you take as input 

```bash
fswatch -0 ./mendeley_output/ | xargs -0 -n1 -I{} echo "{}"
```






TODO check Amoeba splitting of notes (here is a typical application case ... Automatization and sed lines should go in separate notes as these can be used for other purposes than just the .bib reformating)






TODO understand the way to have the bibliography display on the published version of dendron. Not the case at the moment see [[public.project.tramadol]]


