---
id: d9226da2-37e8-45af-b29c-acdf6b66bd58
title: Update
desc: ''
updated: 1609689855656
created: 1609689794407
---

To update a conda environment given a .yml file

https://stackoverflow.com/a/43873901

```bash
conda activate myenv
conda env update --file local.yml
```

Or without the need to activate the environment (thanks @NumesSanguis):

```bash
conda env update --name myenv --file local.yml
````
