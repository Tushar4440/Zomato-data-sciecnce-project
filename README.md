# Zomato Restaurant Data Analysis

A small exploratory data analysis project using a CSV of restaurant listings and a Jupyter notebook. The notebook uses Python, pandas, NumPy, Matplotlib, and Seaborn to inspect the data and visualize restaurant categories, customer votes, ratings, approximate prices, and online-order availability.

## Project At A Glance

- **Analysis:** exploratory, descriptive analysis of restaurant listing data
- **Dataset:** 148 rows and 7 columns
- **Main artifact:** `Zomato_Data_analysis.ipynb`
- **Input data:** `Zomato data.csv`
- **Notebook output:** printed summaries and charts rendered in the notebook
- **Currency and collection date:** not specified in the supplied project files

## Repository Contents

| File | Purpose |
| --- | --- |
| `Zomato_Data_analysis.ipynb` | Notebook containing the analysis code, questions, takeaways, and visualizations |
| `Zomato data.csv` | Restaurant listing data loaded by the notebook |
| `zomato full project Notes.pdf` | Supporting project notes supplied with the workspace |

Keep the notebook and CSV in the same directory. The notebook reads the data using the relative path `Zomato data.csv`.

## Questions Explored

The notebook investigates these questions:

1. Which restaurant listing type appears most often?
2. How many customer votes are associated with each restaurant type?
3. How are restaurant ratings distributed?
4. What is the average approximate cost for two people?
5. How do restaurant ratings compare for listings that do and do not offer online ordering?
6. How does online-order availability vary by restaurant type, and which types have more offline-only listings?

The notebook labels its chart-based observations inline. The figures below are calculated from the CSV currently in the project and are intended as descriptive summaries, not causal conclusions.

## Dataset

The CSV has one row per restaurant listing and the following columns:

| Column | Meaning | Example / notes |
| --- | --- | --- |
| `name` | Restaurant name | `Jalsa` |
| `online_order` | Whether online ordering is available | `Yes` or `No` |
| `book_table` | Whether table booking is available | `Yes` or `No` |
| `rate` | Restaurant rating | Text in an `x.x/5` format; the notebook converts it to a number |
| `votes` | Number of customer votes represented in the data | Integer count |
| `approx_cost(for two people)` | Approximate listed cost for two people | Numeric value; currency is not identified in the supplied files |
| `listed_in(type)` | Restaurant listing category | Includes `Dining`, `Cafes`, `Buffet`, and `other` |

### Verified Snapshot

| Listing type | Restaurant listings | Customer votes | Online ordering: Yes | Online ordering: No |
| --- | ---: | ---: | ---: | ---: |
| Dining | 110 | 20,363 | 33 | 77 |
| Cafes | 23 | 6,434 | 15 | 8 |
| other | 8 | 9,367 | 6 | 2 |
| Buffet | 7 | 3,028 | 4 | 3 |
| **Total** | **148** | **39,192** | **58** | **90** |

Other checks against the supplied CSV:

- Average `approx_cost(for two people)`: **418.24** in the dataset's unspecified currency units.
- Cost range: **100–950**.
- Ratings range: **2.6–4.6** out of 5; the arithmetic mean is approximately **3.63**.
- Dining has the largest number of listings and the largest total vote count.
- Dining listings have more `No` than `Yes` values for online ordering (77 versus 33); Cafe listings have more `Yes` than `No` (15 versus 8).

These figures describe this CSV only. They should not be interpreted as estimates for all Zomato restaurants or all customer orders.

## Analysis Workflow

The notebook follows this sequence:

1. Imports NumPy, pandas, Matplotlib, and Seaborn.
2. Loads the CSV into a pandas DataFrame and inspects sample rows and column information.
3. Converts the `rate` text values to floating-point numbers by taking the part before `/`.
4. Uses a count plot to view the number of records in each restaurant type.
5. Groups by restaurant type and sums `votes`, then plots the totals.
6. Plots a histogram of restaurant ratings.
7. Calculates the mean approximate two-person cost and plots the observed cost values.
8. Compares rating distributions for online-order availability with a box plot.
9. Builds a restaurant-type by online-order cross-tabulation and visualizes it as a heatmap.

## Requirements

- Python 3
- Jupyter Notebook support, such as the Jupyter extension in Visual Studio Code or JupyterLab
- Python packages: `numpy`, `pandas`, `matplotlib`, and `seaborn`

Install the packages in your active Python environment:

```bash
python -m pip install numpy pandas matplotlib seaborn jupyter
```

On some Windows installations, use `py` in place of `python` if that is the Python launcher configured on your machine.

## Run The Analysis

### Visual Studio Code

1. Open this project folder in VS Code.
2. Open `Zomato_Data_analysis.ipynb`.
3. Select a Python kernel with the required packages installed.
4. Run the notebook cells from top to bottom.

### Jupyter From A Terminal

From the project directory, run:

```bash
python -m jupyter notebook Zomato_Data_analysis.ipynb
```

Run the cells in order so the DataFrame `df` and the converted `rate` column exist before the later analyses use them. The source data is read from the current project directory, so keep `Zomato data.csv` beside the notebook.

## Reproducibility And Data Handling

- The notebook reads the CSV directly; it does not modify or export the source file.
- Most analysis steps create charts or display summaries in the notebook rather than saving separate report files.
- The rating conversion expects values whose numeric rating appears before a slash, such as `4.1/5`.
- The dataset's provenance, collection date, geographic coverage, and currency are not documented in the supplied files. Confirm these details before using the results in a decision or presenting them as representative statistics.
- The notebook currently has embedded outputs, but its cells are not marked as executed in the workspace metadata. Re-run all cells to regenerate and verify the displayed results after changing the data or environment.

## Interpretation Notes And Limitations

- This is a compact dataset of 148 restaurant listings, not a transaction-level dataset. It does not show how many orders were placed or what an individual customer spent.
- The approximate cost column describes a listed cost for two people; it is not necessarily the amount paid for a typical online order.
- The notebook's question about what “people order from” is answered using counts of restaurant types in the listings. That is a measure of listing composition, not order volume or customer preference.
- A larger vote total can reflect more listings, more engagement, or both. The totals are not normalized by the number of listings in each category.
- The online-order comparison is observational. It does not establish that online ordering causes higher or lower ratings.
- No time, location, cuisine, order count, or customer-level fields are present in the CSV, so the analysis cannot describe trends over time, geographic patterns, cuisine-specific effects, or individual behavior.
- Values and summaries may change if the CSV is replaced or edited. Re-run the notebook before relying on any figures in this README.

## Possible Extensions

- Add a documented data source, collection date, geographic scope, and currency.
- Check for missing values, duplicate listings, inconsistent categories, and non-numeric or malformed ratings before analysis.
- Compare average ratings and votes per listing alongside category totals.
- Format charts with clearer titles, units, sorted categories, and readable value labels.
- Save cleaned data and charts as explicit outputs if the analysis needs a repeatable reporting workflow.
