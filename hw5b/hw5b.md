```python

```

\begin{center}
\begin{huge}
DATA203 Foundational Python (Prof. Maull) / Fall 2026 / HW5B
\end{huge}
\end{center}

| Points <br/>Possible | Due Date | Time Commitment <br/>(estimated) |
|:---------------:|:--------:|:---------------:|
| 15 | Wednesday, Dec 2 @ midnight | _up to_ 8 hours |


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
* Connecting census tracts with other data.

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
### (100%) Connecting census tracts with other data. 


In HW4 we generated a nice clean and enriched dataset that had a large
number of interesting properties. 

We are going to use what we learned and apply to a different problem.

If you were born after 2005, you are well aware that public libraries
exist, but because you are largely considered a _digital native_, it is
possible that your experience of libraries has be tilted towards their
digital form, rather than their physical form.

But you are no, doubt, aware of the public libraries in your communities
and it is not an unusual question to look at these libraries within the
lens of the communities they serve. We will work within the framework of
SVI from HW4 to complete this assignment.

We will use a variety of libraries from [Pandas](https://pandas.pydata.org/pandas-docs/stable/index.html), [GeoPandas](https://geopandas.org/) and [pygris](https://walker-data.com/pygris) to
dig into the data and ask some interesting questions.

**&#167; Task:**  **1.1 &#8594; Install and import ** `pygris` **and load the census tracts for Washington, DC.**


You will need to run `!pip install` and read the installation
documentation for `pygris`:

*   [pygris](https://walker-data.com/pygris/)

Learn to use the [`tracts()`](https://walker-data.com/pygris/02-geometries/#working-with-geometries-in-pygris) function and then 
build a map of the census tracts with 
[`GeoDataFrame.explore()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.explore.html#geopandas.GeoDataFrame.explore).

You will only have 2 lines of code to accomplish:

1. loading the tracts for Washington, DC into a variable `gdf_dc_tracts`,
2. displaying the Folium map using `explore()` on `gdf_dc_tracts`.  See the examples in the documentation for `pygris`.

Your map will look like:

![](./image1_1.png)

**Hints:**

- pass the parameters `cb = False, cache = True` into `tracts()`;
- the first parameter to `tracts()` will be `"DC"`.


**&#167; Task:**  **1.2 &#8594; Load the library locations file and obtain their Point geometries.  Display the results in a map. **

Use [`pygris.geocode.batch_geocode()`](https://walker-data.com/pygris/04-geocoding/) to get the Point geometries
using the `Address` column of the file `data/dc_public_libraries.csv`.

Store this data into a variable `gdf_libraries`.

Display the results with `.explore()` on `gdf_libraries`.

**Hints:**

- use the examples in the link provided above;
- the first parameter to your `batch_decode` will be `dc_libraries` from the first part;
- use the following additional parameters to `batch_decode(..., id_column="Library", address="Address", as_gdf = True)`;
- pass the parameter `marker_type="marker"` to `explore()`.

Your output will look like:

![](./image1_2.png)


**&#167; Task:**  **1.3 &#8594; Map the census tracts of each library using geometric search.**

You will notice that both `gdf_dc_libraries` and `gdf_tracts` have a
column called `geometry`.  Why?  The answer is simple: GeoPandas is an
extension of Pandas with  the addition of geometries for plotting and
mapping.

What benefit is this?

We can take advantage of these "geometries" to ask GeoPandas
to do some calculations for us, like determining if a Point
is within a Polygon.

Use the [`contains()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.contains.html) function on the `geometry` column
to find and map all the libraries and their census tracts.


Your output will look like:

![](./image1_3.png)

Hints:

- you can use `concat()` to put all the data into 
  a DataFrame -- and you can even go back and 
  forth between Pandas DataFrame and GeoPandas GeoDataFrames;
- if you get errors about CRS mismatches, use `to_crs("NAD83")`;
- don't forget to pass `market_type="marker"` to 
  your final call to `explore()`;
- don't overthink it, this can be done in a single line of code!


**&#167; Task:**  **1.4 &#8594; Create a DataFrame that assigns a GEOID to each library using `dc_tracts` then merge with the SVI data.**

So far we've been making nice pictures but 
we would like to merge data in a way that we
can run some simple analysis over it.

We are going to do this in two parts:

1. create a new DataFrame `gdf_libraries_geoid` which uses
   `contains` from the prior part and merges
   it with `gdf_libraries`,
2. the resulting DataFrame will use `GEOID` and be merged
   with the `data/SVI_DISTRICTOFCOLUMBIA.csv` file on the keys `FIPS`
   (from the SVI data) and `GEOID` from the `gdf_libraries_geoid`
   DataFrame.  You will only need to hold on to the columns `FIPS`,
   `AREA_SQMI`, `E_TOTPOP` and `RPL_THEMES` as shown below.

For part 1. you will have a DataFrame that looks like (the column order is irrelevant):

```
|    | id                             | geometry                                 |       GEOID |
|---:|:-------------------------------:------------------------------------------|------------:|
|  0 | Deanwood Neighborhood Library  | POINT (-76.931735610624 38.908012816812) | 11001007806 |
|  1 | Lamond-Riggs Branch Library    | POINT (-76.999529633395 38.954799047616) | 11001009508 |
|  2 | Northeast Branch Library       | POINT (-76.996235746922 38.893969440099) | 11001008302 |
| ...| ...                            | ...                                      | ... |
```
For part 2. you will have a DataFrame that looks like (again, the column order is irrelevant):

```
|    |        FIPS |   AREA_SQMI | E_TOTPOP |   RPL_THEMES | id                              | geometry                                 |       GEOID |
|---:|------------:|------------:|---------:|-------------:|:--------------------------------|:-----------------------------------------|------------:|
|  0 | 11001000102 |   0.658877  |     3127 |       0.0936 | Georgetown Branch Library       | POINT (-77.065721452114 38.913657091326) | 11001000102 |
|  1 | 11001000600 |   0.556707  |     4548 |       0.2069 | Cleveland Park Branch Library   | POINT (-77.05743946625 38.933586267886)  | 11001000600 |
|  2 | 11001000804 |   0.991034  |     3674 |       0.1330 | Palisades Branch Library        | POINT (-77.09684511879 38.918165723055)  | 11001000804 |
| ...| ...         |         ... |      ... |          ... |            ...                  |                 ...                      |    ...      |          
```

You can use all tools available to you, but here are some hints:

- you will only need the `id` and `geometry` columns from `gdf_libraries`;
- you will find that you can reuse your code from before to look into `dc_tracts` to 
  determine if a particular tract contains a library using `gdf_libraries.geometry`;
- you really only should need to use
[`merge`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.merge.html#pandas.DataFrame.merge) 
  on the DataFrame with the SVI data
  and `gdf_libraries_geoid` and use `left_on="FIPS"` and `right_on="GEOID"` within
  the merge.


**&#167; Task:**  **1.5 &#8594; Get some descriptive stats for the library tracts SVI data.**

Now that you have a nice DataFrame, answer the following questions:

1. What is the _median_ SVI for tracts with libraries in them?
2. Provide a scatter plot of library tracts `AREA_SQMI` plotted 
   against `RPL_THEMES` > 0.60 on the $y$-axis.  Describe what you are
   seeing.  Use
   [`DataFrame.plot.scatter()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.plot.scatter.html#pandas.DataFrame.plot.scatter)
3. True or False. _There are as many library tracts with_ `RPL_THEMES` > 0.60 _than
   those with_ `RPL_THEMES` < 0.30.  You may give the answer based on
   numbers "approximately" within &#177; 2 libraries.  Show your work
   justifying your answer.




