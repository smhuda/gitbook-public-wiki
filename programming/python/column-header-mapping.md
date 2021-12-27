# Column Header Mapping

```text
import pandas as pd

df=pd.read_excel('your_file_name.xlsx')
drop_cols=[,,,]  #list of columns to get rid of
df.drop(drop_cols,axis='columns')

col_dict={'col-a':'col-x','col-b':'col-y','col-c':'col-z'} #however you want to map you new columns in this example abc are old columns and xyz are new ones

#this line will actually rename your columns with the dictionary
df=df.rename(columns=col_dict)

df.to_csv('new_file_name.csv')  #write new file
```



