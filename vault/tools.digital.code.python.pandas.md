---
id: d116d7cc-dbf7-4876-b182-7065c314703e
title: Pandas
desc: ''
updated: 1609846918431
created: 1609770454495
---

## Subset a df according to string present in columns name

```python
df.loc[:, df.columns.str.startswith('alp')]
```

```python
df.loc[:, df.columns.str.contains('alp')]
```

## Rename columns

```python
df.rename(columns={'oldName1': 'newName1', 'oldName2': 'newName2'}, inplace=True)
```

## Check df datatype

```python
df.dtypes
```

## Convert to a specific type

```python
df.year.astype(int)
```
