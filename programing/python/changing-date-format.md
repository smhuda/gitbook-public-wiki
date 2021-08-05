# Changing Date Format

Use `'%Y-%m-%d'`

**Ex:**

```text
import pandas as pd

df = pd.DataFrame({"Date": ["26-12-2007", "27-12-2007", "28-12-2007"]})
df["Date"] = pd.to_datetime(df["Date"]).dt.strftime('%Y-%m-%d')
print(df)
```

**Output:**

```text
         Date
0  2007-12-26
1  2007-12-27
2  2007-12-28
```

