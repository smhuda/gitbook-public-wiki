# Regex - Remove HTML Tags

| Character | Meaning |
| :--- | :--- |
| &lt; | Matches character “&lt;” |
| \[^&lt;\] | Negated set - matches any character that is not in the set. |
| + | Matches one or more of the preceding token |
| ? | If used immediately after any of the quantifiers \*, +, ?, or {}, makes the quantifier non-greedy \(matching the minimum number of times\). |

```text
# Replace all html tags with blank from surveyAnswer column in dataframe df.
# regex=True is the default so you can choose not to explicitly specify it.
df["surveyAnswer"] = df["surveyAnswer"].str.replace('<[^<]+?>','',regex=True)
```

