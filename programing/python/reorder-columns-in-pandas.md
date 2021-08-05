# Reorder Columns in Pandas

### Use double brackets to reorder columns in a DataFrame

Use the syntax `DataFrame[["column1", "column2", "column3"]]` with the column names in the desired order to reorder the columns.

```text
print(df)
```

**Output:**

```text
   A  B  C
0  1  4  7
1  2  5  8
2  3  6  9
```

```text
df = df[["C", "A", "B"]]
print(df)
```

**Output:**

```text
   C  A  B
0  7  1  4
1  8  2  5
2  9  3  6
```

### Use `pandas.DataFrame.reindex()` to reorder columns in a DataFrame

Call `pandas.DataFrame.reindex(columns=column_names)` with a list of the column names in the desired order as `column_names` to reorder the columns.

```text
print(df)
```

**Output:**

```text
   A  B  C
0  1  4  7
1  2  5  8
2  3  6  9
```

```text
column_names = ["C", "A", "B"]
df = df.reindex(columns=column_names)
print(df)
```

**Output:**

```text
   C  A  B
0  7  1  4
1  8  2  5
2  9  3  6
```

