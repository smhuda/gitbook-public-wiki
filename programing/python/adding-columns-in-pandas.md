# Adding Columns in Pandas

### Method 1 <a id="0e8d"></a>

This might be the most commonly used method for creating a new column.

```text
df["C"] = [10, 20, 30, 40]
df
```

### Method 2 <a id="f7dc"></a>

In the first method, the new column is added at the end. Pandas also allows for adding new column at a specific index. The insert function can be used to customize the location of the new column. Let’s add one next to column A.

```text
df.insert(1, "D", 5)
df
```

The insert function takes 3 parameters which are the index, the name of the column, and the values. The column indices start from 0 so we set the index parameter as 1 to add the new column next to column A. We can pass a constant value to be filled in all rows.

### Method 3 <a id="88f0"></a>

The loc method selects rows and columns using their labels. It is also possible to create a new column with this method.

```text
df.loc[:, "E"] = list("abcd")
df
```

In order to select rows and columns, we pass the desired labels. The colon indicates that we want to select all the rows. In the column part, we specify the labels of the columns to be selected. Since the data frame does not have column E, Pandas creates a new column.

### Method 4 <a id="6e2f"></a>

The last method is the assign function.

```text
df = df.assign(F = df.C * 10)
df
```

We specify both the column name and values inside the assign function. You may notice that we derive the values using another column in the data frame. The previous methods also allow for such derivations.

There is an important difference between the insert and assign functions. The insert function works in place which means the change \(adding new column\) is saved in the data frame.

