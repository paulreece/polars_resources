
### **`with_columns`**<br/> 
Return a version of your df back including all of it's columns. An argument is required, even if you're just selecting a column.<br/> 
It's important to know for many operations used in cleaning Data.
```Ruby
combined_df.with_columns(your_argument)
combined_df.with_columns(Polars.col("selected_column"))
```
### `Polars.col` vs df["column_name"]
`Polars.col` selects your specified column from the DataFrame and returns a Dataframe(if used on a DataFrame).  I recommend this as the go to for most cleaning Data operations.

```Ruby
irb(main):> combined_df.select(Polars.col("year"))
=>
shape: (6, 1)
┌──────┐
│ year │
│ ---  │
│ i64  │
╞══════╡
│ 1984 │
│ 1985 │
│ 1993 │
└──────┘
```
`df["column_name"]`<br/> 
When doing mathematical operations(excluding comparisons <, > etc) and transforming values with a hash, we want a series, so use square brackets. For everything else try to use Polars.col as a default
Returns a Series.  Mainly used in column-wise operations.
```Ruby
irb(main):> combined_df["year"]
=>
shape: (6,)
Series: 'year' [i64]
[
	1984
	1985
	1993
	1993
	2010
	1999
]
```

### Turning JSON into a DataFrame
```Ruby
Polars::DataFrame.new(json_response["response"]["data"])

```

### Renaming All Columns
```Ruby
df.columns = ["your", "new", "column", "names"]

```

### Renaming a Single or Multiple Columns
```Ruby
df.rename({"foo" => "apple"})
df.rename({"foo" => "apple", "bar" => "orange"})
```

### Finding Null and Nan

```Ruby
df.null_count

#Count of all the NaNs
nan_cols = df.columns.filter_map { |col|  col if df[col].is_numeric}
df.select(Polars.col(nan_cols).is_nan.sum)

#Specific Columns wiht NaN
df.filter(Polars.col("column_name").is_nan())

```
### Filling Null and Nan

```Ruby
df = df.with_columns(Polars.col("column_name").fill_null(Polars.lit("Value")))

df = df.with_columns(Polars.col("column_name").fill_nan(7.5))

```
### Dropping Null and Nan
```Ruby
df.drop_nulls()
df.drop_nans()
```
### Filtering
```Ruby
df.filter(Polars.col("column_name") == Value)
```
### Add Column
```Ruby
#Insert same value in each column
df.with_columns(Polars.lit("Value").alias("column_name"))

#Insert a Series of Values as new column
df.with_columns(your_series.alias("column_name"))
)
```

#Removing Columns
```Ruby
#Remove a single column
df = df.drop("column_name")

#Remove multiple columns
df = df.drop(["column_one", "column_two"])
```
### Convert String column to DateTime
```Ruby
df.with_columns(Polars.col("date_added").str.to_datetime(format = "%m/%d/%Y", time_unit: "ns"))
```
### Combining DataFrames
```Ruby
# Add rows to first DataFrame from second
df = df.vstack(df_two)

#Add columns to first DataFrame from second
df = df.hstack(df_two)

# Join
df = df.join(df_two, on="column_name", how=["inner", "left" "outer", "semi" "anti" "cross"])
```

### Dropping Duplicates
```Ruby
df = df.unique(subset:["column_name"])
```
### Creating Month column from DateTime column
```Ruby
df = df.with_columns(Polars.col("date").month.alias("month"))
```

### Converting Column Values with Hash from one type to another
```Ruby
month_hash = {1 => "January", 2 => "February", 3 => "March", 4 => "April", 5 => "May", 6 => "June", 7 => "July", 8 => "August", 9 => "September", 10 => "October", 11 => "November", 12 => "December"}
month_names = Polars::Series.new(combined_df.select(Polars.col("month")).rows.map{ |k| month_hash[k[0]] })
df = df.with_columns(month_names.alias("month"))
```

### Creating Charts
```Ruby
#Add to Gemfile and install  
gem "vega"  
 
#Install and import JS dependencies
import "vega”
import "vega-lite”
import "vega-embed”

# In controller  
def index
  @movie_df = Polars::DataFrame.new(Movie.all)
end

#In erb/template file  
<%= @movie_df.plot("name", "rank", type: ”line")
```

### Column-wise Operations
```Ruby
# Single Column
df["column_name"] * value
df["column_name"] / value
df["column_name"] - value
df["column_name"] + value

# Operations on columns with column
df["column_one"] * df["column_two"]
df["column_one"] / df["column_two"]
df["column_one"] - df["column_two"]
df["column_one"] + df["column_two"]
```
