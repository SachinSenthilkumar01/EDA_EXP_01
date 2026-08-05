# Experiment 1: Exploratory Data Analysis (EDA) on IPL Dataset

## Aim
To perform Exploratory Data Analysis (EDA) on the IPL matches dataset and derive insights about:

- Matches played per season
- Top winning teams
- Toss decision preferences
- Stadiums hosting the maximum matches

---

## Algorithm / Procedure

### Step 1: Import Libraries
- Import **pandas** for data manipulation.
- Import **matplotlib.pyplot** and **seaborn** for data visualization.

### Step 2: Load Dataset
- Load the IPL matches dataset using `pd.read_csv()`.
- Check the dataset dimensions using `.shape`.
- Display the first five rows using `.head()`.

### Step 3: Matches per Season (Univariate Analysis)
- Group the dataset by **season**.
- Count the total number of matches played in each season.
- Visualize the results using a **bar chart**.

### Step 4: Top Winning Teams (Univariate Analysis)
- Count the number of wins for each team using the `winner` column.
- Display the **Top 5 winning teams**.
- Visualize the results using a **bar chart**.

### Step 5: Toss Decisions (Univariate Analysis)
- Count the frequency of toss decisions (`bat` and `field`).
- Visualize the distribution using a **bar chart**.

### Step 6: Stadiums Hosting Maximum Matches (Univariate Analysis)
- Count the number of matches hosted by each stadium using the `venue` column.
- Display the **Top 5 stadiums** with the highest number of matches.
- Visualize the results using a **horizontal bar chart**.

### Step 7: Draw Insights
- Observe trends in the number of matches played across seasons.
- Identify the most successful IPL teams.
- Analyze teams' preferred toss decisions.
- Highlight the stadiums that have hosted the highest number of IPL matches.

---

## Program

```python
# Write your code here
```

---

## Output

Add screenshots of the following outputs:

- Dataset preview (`head()`)
- Matches per Season Bar Chart
- Top Winning Teams Bar Chart
- Toss Decision Bar Chart
- Stadiums Hosting Maximum Matches Horizontal Bar Chart

---


---

## Result

The Exploratory Data Analysis (EDA) on the IPL matches dataset was successfully performed. Various visualizations were created to analyze seasonal trends, winning teams, toss decisions, and the stadiums hosting the highest number of matches.
