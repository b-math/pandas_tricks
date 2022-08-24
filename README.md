# Tricks for reocurring pandas problems


## Select all rows with substring in column

Select all rows from pd.DataFrame `df` containing the substring `substr` in the colum `col`.

    df.loc[df['col'].str.contains("substr", case=False)]
    
## Select all columns having substring in column name

Select all columns from pd.DataFrame `df` containing the substring `substr` in the column name.

    df[[i for i in df.columns if "substr" in i]]

## write custom header "header" when exporting pd.DataFrame "df" into file "file_path".

    with open(file_path, 'w') as f:
		f.write(header)
    df.to_csv(file_path, header=False, mode="a")
