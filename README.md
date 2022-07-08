# Tricks for reocurring pandas problems


## Select all rows with substring in column

Select all rows from pd.DataFrame `df` containing the substring `substr` in the colum `col`.

    df.loc[df['col'].str.contains("substr", case=False)]
