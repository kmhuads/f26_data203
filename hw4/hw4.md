```python

```

\begin{center}
\begin{huge}
DATA203 Foundational Python (Prof. Maull) / Fall 2026 / HW4
\end{huge}
\end{center}

| Points <br/>Possible | Due Date | Time Commitment <br/>(estimated) |
|:---------------:|:--------:|:---------------:|
| 20 | Tuesday, Nov 16 @ midnight | _up to_ 8 hours |


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
* Data munging and preparation in Python and Pandas.

* Explore and graph data from the enriched dataset.

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
then upload the `.zip` to Teams.

If are confused on how to do this, please ask, 
or visit one of the many tutorials
on the basics of using zip in Linux.  

If you choose not to use the provided notebook, you will still need to turn in a
`.ipynb` Jupyter Notebook and corresponding files according to the instructions in
this homework.


## ASSIGNMENT TASKS
### (75%) Data munging and preparation in Python and Pandas. 


We learned about data engineering and
"data munging" in lecture, and there 
are typically 5 steps to this process:

1. _Data discovery_: finding datasets containing the relevant data of interest;
2. _Structuring_: combining and choosing the data needed;
3. _Cleaning_: removing data that is of poor quality or low relevance;
4. _Enriching_: converting and combining existing data to new data;
5. _Verifying_: certifying the final dataset has the data necessary of sufficient quality.

We're going to skip over 1) for now but use the main tool at our disposal (Pandas)
to instead work through a little bit of 2, 3, and 4.  The main task will be 
to explore a selected dataset which has interest and value among many disciplines.

The U.S. CDC's (Center for Disease Control and Prevention) Agency for
Toxic Substances and Disease Registry (ATSDR) is an oversight and
advisory agency within the U.S. Department of Health and Human Services
(HHS) dedicated to evaluating hazardous substance effects on public
health. Its primary functions include assessing hazards at Superfund
sites, conducting public health assessments for specific waste
facilities, managing long-term surveillance studies, and responding to
emergency releases of toxic materials. Additionally, ATSDR supports
environmental regulation by preparing detailed toxicological profiles
and providing education on preventing exposure-related illnesses.

As you may already know the U.S. EPA (Environmental Protection Agency) is
the agency responsible for overseeing comprehensive activities
including environmental assessment, research, and education to ensure
compliance with federal regulations. Working collaboratively with state,
tribal, and local authorities, it maintains national standards under
various U.S. laws by implementing enforceable actions such as fines and
sanctions for non-compliance.

One of the principal differences between the two organizations is
enforcement, which is the EPAs _primary_ directive and not within
the capability of ATSDR.

We are going to combine data from both
of these agencies in this and the next homework.

The first dataset we will learn about
is maintained by ATSDR and is based on what is called the 
CDC/ATSDR Social Vulnerability Index (CDC/ATSDR SVI or SVI).
In this dataset are a vast number of variables
about the socioeconomic variables in the U.S.,
specifically from their website, "social vulnerability" is explained as:

> "... the demographic and socioeconomic factors (such as poverty, lack of access to 
  transportation, and crowded housing) that adversely affect communities that encounter 
  hazards and other community-level stressors ..."


This dataset is of interest because of its value
in understanding the granular impacts of environmental
policies at the community level -- including the _historical_ 
lens required to understand _how_ those impacts have manifest.  We will
be using the _census tract_ level of data for a subset 
of the U.S. to perform **exploratory data analysis**.

You will need to learn more about and study this dataset here:

* [CDC/ATSDR Social Vulnerability Index website](https://atsdr.cdc.gov/place-health/php/svi/index.html)

**&#167; Task:**  **1.1 &#8594; [Structuring] Use the provided files in `data/` and combine them with Pandas and export to a CSV.**

There are four files in `data/`:

* CALIFORNIA.csv
* TEXAS.csv
* VERMONT.csv
* WYOMING.csv

These files contain the SVI census data for 2022 and include data
about population and community characteristics. It is not a mistake
that these are the two _most_ and _least_ populous states in the
contiguous lower 48 U.S. states.

Here are some hints for this task: 

* You will use Pandas [`pandas.read_csv()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_csv.html#pandas.DataFrame.read_csv) to merge these
files into one csv called `data/hw4_CA_TX_VT_WY_SVI_census_tract.csv`.          

* Use Pandas [`pandas.to_csv()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_csv.html#pandas.DataFrame.to_csv).

* You may also find Pandas [`pandas.concat()`](https://pandas.pydata.org/docs/reference/api/pandas.concat.html#pandas.concat) extremely useful.


**&#167; Task:**  **1.2 &#8594; [Cleaning] Clean your CSV file be removing any row of data that contains the value `-999`.  Export the cleaned data to a CSV.**

When you look into the data bit, you will see there are some 
wonky values -- stuff that does not seem to belong, such as  values
like `-999`.  We don't want that in our data.

You will remove all lines (rows) which contain a `-999` 
in _any_ field.  After doing so, use `pandas.to_csv()` to write the 
data to a _new_ file called `data/hw4_CA_TX_VT_WY_SVI_census_tract_cleaned.csv`.

Here are some hints:

* You may find that looping over all rows and columns to be inefficient.
* There is an efficient one-liner solution if you study [`DataFrame.isin()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.isin.html#pandas.DataFrame.isin) and [`DataFrame.any()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.any.html#pandas.DataFrame.any).  Both of these may be valuable.
* You may also want to study [`DataFrame.apply()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.apply.html#pandas.DataFrame.apply) and combine it with `isin()`.
* Your original dataset has 16346 rows, the new dataset will have 16223 rows.


**&#167; Task:**  **1.3 &#8594; [Enriching] Load the cleaned file and produce a new derived column.**

Using your now cleaned data, we will continue an enrichment of use.

You will notice there are two columns in the data `E_TOTPOP` and `AREA_SQMI`.

These two variables are very useful, but even more useful is the
_population per square mi_, which is absent from the original data.
Luckily, this calculation is easy to produce by simply dividing the
population by the area in square miles of the census tract.  Just
remember, we are looking at _tract level_ data, and each tract
typically contains 3000-6000 people in it, but the _physical size_ of
each tract in square miles varies substantially.

Your DataFrame must have the new derived column named `POP_PER_SQMI`
which is just  `E_TOTPOP` divided by `AREA_SQMI`. 

Hints:

- You can get a column of data from a DataFrame using the [`DataFrame.get()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.get.html#pandas.DataFrame.get), [`DataFrame.loc()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.loc.html#pandas.DataFrame.loc)   functions or even the `[]` selector; 
  all of these will get what you need. 
- Recall our discussion about doing math with Series and DataFrames, it will guide your solution.
- Using `pd.concat` (or other means) you can put the new data back into the `POP_PER_SQMI` of the DataFrame.
- Don't overthink it!


**&#167; Task:**  **1.4 &#8594; [Enriching] Add a new column which represents the type of the census tract.**

Knowing the population per square mile allows
us to derive whether a census tract is urban, rural or something
in between or in the extremes. 

Use the provided function in the starter notebook `compute_tract_density()`
and use the Pandas [`DataFrame.apply()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.apply.html#pandas.DataFrame.apply)
function to obtain the designated
density of the tract.


Store the newly assigned computation in a column
called `DENSITY_TYPE`.


**&#167; Task:**  **1.5 &#8594; [Enriching] Save the enriched and reduced file.**

You will notice there are over 150 _columns_ of variables in the dataset!

While many of these variables are useful, we will not be able (or want) to use
them all.  Let's subset this down to the variables with the most interest
to us right now.

We would like to have a file with the ONLY following 14 columns:

* `ST_ABBR`
* `COUNTY`
* `FIPS`
* `AREA_SQMI`
* `E_TOTPOP`
* `E_HU`
* `EPL_CROWD`
* `EP_AGE65`
* `EP_MINRTY`
* `EP_MUNIT`
* `EP_POV150`
* `EP_NOHSDP`
* `RPL_THEMES`
* `POP_PER_SQMI` (your new calculated variable from 1.3)
* `DENSITY_TYPE` (your calcation from 1.4)

Save the data to a file `data/hw4_CA_TX_VT_WY_SVI_census_tract_cleaned_enriched_subsetted_final.csv`.

Hints: 

* You can use `DataFrame.get()`, `.loc()` and other methods to subset the columns
* As per usual, use `DataFrame.to_csv()`.



### (25%) Explore and graph data from the enriched dataset. 


Now that we have a nice clean and enriched dataset in 

* `data/hw4_CA_TX_VT_WY_SVI_census_tract_cleaned_enriched_subsetted_final.csv`

we would like to start exploring some of the patterns
in the data.

We often like to get _descriptive_ statistics
about our data and Pandas will allow us 
to answer a number of basic questions
rather easily.

Furthermore, Pandas offers a variety of plotting functions
to see the data visually instead of looking at tables
and numbers.  Pretty pictures also help us to see 
and communicate patterns to others who may not be 
domain experts or understand the data as well
as you do.

We are going to do both.

**&#167; Task:**  **2.1 &#8594; Use Pandas `describe()` to determine the median population and area in the data.**

* Write the code which shows the median `POP_PER_SQMI` and `AREA_SQMI` for each of CA, TX, VT and WY 
 (it may be easier to put them in one table if you like).
* Write your observations about your findings about the `AREA_SQMI` differences between these variables. 
* Explain why the following statement is _True_ or _False_:
  * _On average, Wyoming census tracts are over 10 times more area than those in Vermont._
  * You must use direct evidence from your findings to support your answer.


**&#167; Task:**  **2.2 &#8594; Produce  scatter plots showing the `RPL_THEME` vs `EP_MINRTY` for urban and rural density types for each state.**

* Use `DataFrame.plot.scatter()` where the $x$-axis is the `RPL_THEME` and $y$-axis is the `EP_MINRTY`.
* You will have 8 graphs, two for each state (one urban, one suburban).
* You may combine the urban and suburban into one graph as long as they are
  properly colored (one must be a different color than the other).

Hints:

* You must use the newly created `DENSITY_TYPE` to filter the data.
* Study the [ `DataFrame.plot.scatter()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.plot.scatter.html)
  function to make your graphs.
* Use the `title=` parameter to label your graphs such as `TX-Urban` for the Texas urban graph and so on.




