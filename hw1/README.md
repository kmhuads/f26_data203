**Homework 1 (HW1)** focuses on using Python to compare and merge two different lists of "Top 25 Best Hip Hop Albums" from online sources.

### Assignment Goal
The overall goal of this assignment is to use Python, specifically working with JSON and YAML data structures, to explore the differences and similarities between two ranked lists of hip-hop albums, focusing on the "Golden Era" (late 1980s through the 90s).

### Data Sources
The homework requires you to work with two hypothetical datasets based on the provided files.

### Objectives to Master:

The assignment is broken down into five main parts, each testing a different skill:

*   **0% Ungraded Practice:** Familiarizing yourself with Jupyter Shell commands (`!mkdir`, `!cat`, `!wget`) for basic file and remote operations.
*   **20% Part 1: Loading Data (JSON/YAML):** Learning how to load data from external files using the `json` and `yaml` modules (`json.load()` and `yaml.safe_load()`). Understanding the structural differences between JSON (key-value maps) and YAML (indented, human-readable).
*   **20% Part 2: Comparing Data with Loops:** Using `for` loops to iterate over the loaded dictionary data (`ds1_yaml` and `ds2_json`) to print ranked lists in specified formats and calculate the average year of albums from each list.
*   **20% Part 3: Comparing Data with Sets:** Using Python **sets** and the `intersection()` method to find common elements (artists and album titles) between the two datasets, highlighting discrepancies.
*   **20% Part 4: Aligning Data into a Single Dictionary:** Structuring the disparate data from both files into a single, unified dictionary (`aligned_full_data`) where each ranking number links an "HHGA" list item to an "SL" list item.
*   **20% Part 5: Merging for the Golden Era:** Creating a final merged list of all unique albums from **both** lists that fall within the **1990s (1990-1999)**, ensuring no duplicates are included.

