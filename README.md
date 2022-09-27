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

## Sort column col in pd.DataFrame df by chromosome

	df[col] = pd.Categorical(df[col], ["chr1", "chr2", "chr3", "chr4", "chr5", "chr6", "chr7", "chr8", "chr9", "chr10", "chr11", "chr12", "chr13", "chr14", "chr15", "chr16", "chr17", "chr18", "chr19", "chr20", "chr21", "chr22", "chrX", "chrY"])
	df = df.sort_values([col])
