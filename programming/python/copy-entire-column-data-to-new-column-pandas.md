# Copy Entire Column Data To New Column Pandas

### Example 1:

I have an excel file containing a column of 'Usernames' and I want to copy-paste that data into the adjacent column in the same sheet and call it 'Passwords'. 

```text
df = pd.read_excel('testsheet.xlsx')

df['password'] = df['username']

df.to_excel("testsheet.xlsx", index=False)
```

