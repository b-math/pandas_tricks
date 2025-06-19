# Tricks for reocurring pandas problems


## Select all rows with substring in column

Select all rows from pd.DataFrame `df` containing the substring `substr` in the colum `col`.

    df.loc[df['col'].str.contains("substr", case=False)]
    
## Select all columns having substring in column name

Select all columns from pd.DataFrame `df` containing the substring `substr` in the column name.

    df[[i for i in df.columns if "substr" in i]]

## Drop all column having substring in column name

Drop all columns from pd.DataFrame `df` containing the substring `substr` in the column name.

    df.drop(list(df.filter(regex='substr')), axis=1, inplace=True)

## write custom header exporting pd.DataFrame

write custom header "header" when exporting pd.DataFrame "df" into file "file_path".

    with open(file_path, 'w') as f:
		f.write(header)
    df.to_csv(file_path, header=False, mode="a")

## Sort column by chromosome

Sort column col in pd.DataFrame df by chromosome

	df[col] = pd.Categorical(df[col], ["chr1", "chr2", "chr3", "chr4", "chr5", "chr6", "chr7", "chr8", "chr9", "chr10", "chr11", "chr12", "chr13", "chr14", "chr15", "chr16", "chr17", "chr18", "chr19", "chr20", "chr21", "chr22", "chrX", "chrY"])
	df = df.sort_values([col])

## Apply function, taking multiple columns as Argument

Apply function "fun" to pd.DataFrame "df", by taking columns "col1" and "col2" as arguments and return in column "outcol"

	def fun(col1, col2): #exemplary
		return col1+col2
		
	df[outcol] = df.apply(lambda x: fun(x.col1, x.col2), axis=1)

Hint: use x.name to select index as input to lambda

## Apply function on pd.DataFrame returning multiple values in separate outcolumns

Apply function "fun" on column "col" in pd.DataFrame "df", returning multiple values. These values are saved in a separate column each ("outcol1", "outcol2")

	def fun(col): #examplary
		return col, col+1
		
	df[[outcol1, outcol2]] = df.apply(lambda x: fun(x.col), axis=1, result_type='expand')
	
Hint: use x.name to select index as input to lambda
	
## Filter column with list

Filter column "col" in pd.DataFrame "df" based on list "list".


## statistics on dataframes

VS code extension "data wrangler"

	df = df[df[col].isin(list)]
