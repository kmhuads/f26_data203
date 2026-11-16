```python

```

\begin{center}
\begin{huge}
DATA203 Foundational Python (Prof. Maull) / Fall 2026 / HW5A
\end{huge}
\end{center}

| Points <br/>Possible | Due Date | Time Commitment <br/>(estimated) |
|:---------------:|:--------:|:---------------:|
| 15 | Wednesday, Dec 3 @ midnight | _up to_ 8 hours |


* **GRADING RUBRIC:** Grading will be aligned with the completeness of the objectives.

	Your solution is evaluated on:

	1. whether your solution correctly answers the question(s) being asked,
	2. using the Python language as required in the question(s).

	Your solution is **NOT** evaluated on:

	1. the elegant use of Python,
	2. optimal or high performance Python code unless _explicitly noted_ in the question(s).

* **INDEPENDENT WORK:** Copying, cheating, plagiarism  and academic dishonesty _are not tolerated_ by University or course policy.  Please see the syllabus for the full departmental and University statement on the academic code of honor.

* **LARGE LANGUAGE MODEL (LLM) / ARTIFICIAL INTELLIGENCE/LLM (AI) POLICY:**

	LLMs / Artificial Intelligence technologies such as 
	Claude, Gemini, Grok, etc are **NOT**
	to be used in the production of your final homework solutions.

	Such technologies offer important capabilities for your 
	_learning_ journey, but they are not appropriate in
	this course for the production of your solutions.

	You _may_ use such technologies to _learn_ more about
	specific Python concepts or to help clarify your
	knowledge about the details of Python syntax, modules, 
	techniques or other programming principles.

	Final solutions found to be the _partial or entire product_ of 
	LLM/AI use **will receive 0 points**, without clarification,
	resubmission or correction.



## OBJECTIVES
* Exploring the ChocoDB data further

## WHAT TO TURN IN
You will enjoy the highest benefits of the starter notebook
if you clone the HW Github repository from your Jupyter Hub
terminal with the command:

```bash
  git clone https://github.com/kmhuads/f26_data203.git
``` 

If you have already cloned the notebook, go to the folder
where you cloned it, open your Jupyter terminal, and
type:

```bash
git pull
```

This will ensure you have the most updated files and starter 
notebook.

Once you have cloned or pulled the repository, you can edit the
starter notebook with your solution code.

When you are done with your work, it will be best to zip
your `hw2` folder and all sub-folders with the terminal command
(one level outside your notebook folder):

``` bash
  zip -r data203_hw4_maull.zip ./hw4
 ```

This will produce the file with all necessary supporting files
(notebooks, data output, etc.) 
then
download it from the Jupyter Hub to your local machine, 
then upload the `.zip` to Canvas.

If are confused on how to do this, please ask, 
or visit one of the many tutorials
on the basics of using zip in Linux.  

If you choose not to use the provided notebook, you will still need to turn in a
`.ipynb` Jupyter Notebook and corresponding files according to the instructions in
this homework.


## ASSIGNMENT TASKS
### (100%) Exploring the ChocoDB data further 


In HW3 we did explore the Flavors of Cacao dataset in detail with an eye
on using Python directly without the use of other libraries.

Now that we have been exposed to Pandas, it is time to use it and see
how much simpler things could be. That simplicity then allows us to get
into other more complex things rapidly. We're going to get into it here
and really take advantage of Pandas to move this dataset towards one
that is truly useful for more advanced exploratory analysis and even
machine learning.

**&#167; Task:**  **1.1 &#8594; Load and reshape the `data/chocodb.csv` data from HW3 using Pandas.**

You will use Pandas [`pandas.read_csv()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_csv.html#pandas.DataFrame.read_csv).

* remember that all the data was quoted so you may find the `quoting` paramater to `read_csv` useful.

You must do the following to your DataFrame and then save the new data into `data/chocodb_reshaped.csv`:

1. remove the `Review Date` and `Ingredients`columns,
2. convert the `Cocoa Percent` to a number like `0.76` for `"76%"` -- the column is a `str` when first loaded,
3. normalize the `Country of Bean Origin` and `Company Location` attributes by making them lowercase and 
   removing extranous spaces at the beginning and end of the string.


**&#167; Task:**  **1.2 &#8594; Run descriptive analytics on the new data.**

Load your reshaped file and use Pandas to answer the following questions:

1. What was the _most frequent_ `Review Date` (i.e. 2000)?
2. What is the overall _mean_ of `Cocoa Percent`?
3. How many reviews include _Madagascar_ as the `Country of Bean Origin`?
4. What is the combined _median_ `Rating` of the seven Central American countries: Belize, Costa Rica, El Salvador, Guatemala, Honduras, Nicaragua, and Panama?
5. True or False: _Looking just at the_ **`Ratings`** _and_ **`Company Location`** _in this dataset, chocolates 
   with companies from_ `Dominican Republic` _have a higher mean rating than those from_ `Portugal`_?_  Show your
   evidence in code.

**Here are some hints:**

* Study [`DataFrame.nlargest()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.nlargest.html) and [`DataFrame.value_counts()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.value_counts.html) as they might be helpful in multiple contexts; 
* [`DataFrame.mean()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.mean.html) and [`DataFrame.median()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.median.html) can be used instead of [`DataFrame.describe()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.describe.html);
* study [`DataFrame.groupby()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.groupby.html) it will make question #5 a little easier, though it is not a requirement;
* as always, don't overthink it and use method chaining for simpler solutions!


**&#167; Task:**  **1.3 &#8594; Enrich the data to produce a set of new derived columns from `Most Memorable Characteristics`.**

This part is going to be a little challenging, but rewarding when you are done.

You will notice that the `Most Memorable Characteristics` are in one string,
meaning that if you wanted to study a cluster of characteristics,
you would be in for a significant challenge.  Furthermore, to do more advanced
data mining and machine learning, this column is an "unmitigated" mess of 
dirty, but useful data.

You are going to fix that.  You will convert the single 
column to multiple columns, in fact, over 1000 of them:

1. take every entry in every row of the `Most Memorable Characteristics` column and split 
   each characterstic along the commas,
2. convert all of the split characteristics to new columns in a new empty DataFrame,
3. you will end up with a DataFrame with nearly 1095 columns, all with the names of the characteristics,
   the DataFrame will initially be empty.

**Hints:**

- There are a variety of ways to get at all the characteristics, one being to write a function 
  that splits all the characteristics by commas, normalizes their strings and strips extra whitespace;
- you may use the `str` functions in Pandas, study them as they will make things much easier.


**&#167; Task:**  **1.4 &#8594; Convert all rows to represent the characteristics as a binary value in a single DataFrame.**

We are in the home stretch.

Now that you have a DataFrame with all the column names as characteristics let's
fill it with data. To do this, you will take all the rows from the original dataset, 
convert the `Most Memorable Characteristics` in the row to 
a DataFrame where the columns are the name of the characteristic
found and the values in the DataFrame are set to  `1`.

For example, if the string in `Most Memorable Characteristics` is
`"cocoa, vegetal, savory"` then your code will produce a new
DataFrame:

| | cocoa | vegetal | savory |
|:--: | :--: | :--: | :--: |
| | 1 | 1 | 1 |

Once you have this DataFrame, you will find
[`pd.concat()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.concat.html)
the perfect tool for adding it into the DataFrame we're trying to
build.  In fact, for the naive case, all you will need to do is
concatenate each row to the empty DataFrame of all characteristics
built in the previous part.

**Hints:** 

- Looping over all rows, will produce the final DataFrame
of `1`s and `NaN`s.  You can repeatedly use `concat()`
to build the final DataFrame just know that this will take some time.
Doing things this way _is_ inefficient, but it demonstrates
the tools that you should become familiar with and reenforces
an important mental model around concatenation of DataFrames
and Series; 
- you may receive a warning about concatenting 
DataFrames with `NaN` values being deprecated.  You can ignore
that for this assignment;
- you will need to execute [`DataFrame.reset_index()`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.reset_index.html) to return the indices
back to the DataFrame -- this is the only linkage back to
your prior data and an important one to have.


An advanced approach to the solution might take advantage of [`DataFrame.explode()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.explode.html),
[`Series.str.get_dummies()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.str.get_dummies.html#pandas.Series.str.get_dummies) and [`DataFrame.groupby()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.groupby.html#pandas.DataFrame.groupby).  It is more efficient, 
but utilizes tools we are yet unfamiliar with at this stage.


**&#167; Task:**  **1.5 &#8594; Reduce the columns to only those with more than 11 rows.**

Now that we have a very large DataFrame (matrix) of `1`s and `NaN`s we
can go ahead and convert the `NaN`s to `0`.  Furthermore, over 1000
columns, with mostly `0`s is an unnecessary burden.  You will notice
that only usually only 3 were used to describe a chocolate --
unfortunate, but a stark reminder that these human curated datasets
are already challenging to generate.

We are going to find only the characteristics that have at least 12
rows (distinct chocolate bars) to represent. Doing this is easier
than you think and the [`DataFrame.sum()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.sum.html#pandas.DataFrame.sum) function will come in
handy.

**Hints:**

- First apply [`DataFrame.fillna()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.fillna.html#pandas.DataFrame.fillna) so that all `NaN` values are `0`;
- you can use `sum()` on the DataFrames of `1`s and `0`s
to find the index of the rows that reach the
threshold of > 11;
- use `iloc[]` with those indices to reduce the 
DataFrame to the rows that you found.


**&#167; Task:**  **1.6 &#8594; Save the reduced DataFrame of 1's and 0's.**

We have just performed and operation called "binarization" and this is
a very useful thing to do with categorical and nominal data as found
in the column of characteristics. Once this is completed, we need to
store it for future use in algorithms and tools which can take this
seemingly uninteresting data and bring it to life. 

Save the DataFrame to a file called: `data/chocodb_features_matrix.csv`.




