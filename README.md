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
import pandas as pd
import matplotlib.pyplot as plt

matches = pd.read_csv("matches.csv")

print("A. Understanding the Dataset")

print("Rows and Columns:", matches.shape)
print(matches.head())
print(matches.columns)
print(matches.dtypes)
print("Unique IDs:", matches["id"].nunique())
print("Total Rows:", len(matches))

print("\nB. Data Quality and Cleaning")

print(matches.isnull().sum())
print("Duplicate Rows:", matches.duplicated().sum())

matches = matches.drop_duplicates()

matches["winner"] = matches["winner"].fillna("No Result")
matches["player_of_match"] = matches["player_of_match"].fillna("Unknown")

if "method" in matches.columns:
    matches["method"] = matches["method"].fillna("Normal")

matches["result_margin"] = matches["result_margin"].fillna(0)

print(matches.isnull().sum())

print("\nC. Matches per Season")

season_matches = matches.groupby("season")["id"].count()

print(season_matches)
print("Season with Highest Matches:", season_matches.idxmax())
print("Number of Matches:", season_matches.max())

season_matches.plot(kind="bar", figsize=(10,5))
plt.title("Matches per Season")
plt.xlabel("Season")
plt.ylabel("Matches")
plt.show()

print("\nD. Top Winning Teams")

wins = matches["winner"].value_counts()
print(wins)

top5 = wins.head(5)
print(top5)

top5.plot(kind="bar", figsize=(8,5), color="green")
plt.title("Top 5 Winning Teams")
plt.xlabel("Team")
plt.ylabel("Wins")
plt.show()

print("\nE. Chennai Super Kings Wins")

csk = matches[matches["winner"] == "Chennai Super Kings"]
print(csk)
print("Total Wins:", len(csk))

print("\nF. Toss Decision Analysis")

toss = matches["toss_decision"].value_counts()
print(toss)

toss.plot(kind="bar", color=["orange","blue"])
plt.title("Toss Decision")
plt.xlabel("Decision")
plt.ylabel("Count")
plt.show()

print("\nG. Pivot Analysis")

pivot = pd.crosstab(matches["season"], matches["toss_decision"])
print(pivot)

pivot.plot(kind="bar", figsize=(10,5))
plt.title("Season-wise Toss Decision")
plt.xlabel("Season")
plt.ylabel("Count")
plt.show()

print("\nH. Venue Analysis")

venue = matches["venue"].value_counts()
print(venue)

top5_venue = venue.head(5)
print(top5_venue)

top5_venue.plot(kind="bar", figsize=(10,5), color="purple")
plt.title("Top 5 Venues")
plt.xlabel("Venue")
plt.ylabel("Matches")
plt.show()

print("\nI. Winning Margin Analysis")

print("Largest Winning Margin:", matches["result_margin"].max())

largest = matches[matches["result_margin"] == matches["result_margin"].max()]
print(largest)

top10 = matches.sort_values(by="result_margin", ascending=False).head(10)
print(top10[["season","team1","team2","winner","result_margin"]])

print("\nJ. Match Result Analysis")

def win_type(result):
    if result == "runs":
        return "Won by Runs"
    elif result == "wickets":
        return "Won by Wickets"
    elif result == "tie":
        return "Tie"
    else:
        return "No Result"

matches["win_type"] = matches["result"].apply(win_type)

print(matches["win_type"].unique())

result_count = matches["win_type"].value_counts()
print(result_count)

result_count.plot(kind="bar", figsize=(7,5), color=["skyblue","lightgreen","orange","red"])
plt.title("Match Result Types")
plt.xlabel("Result Type")
plt.ylabel("Matches")
plt.show()

print("\nK. Basic Data Transformation")

matches["date"] = pd.to_datetime(matches["date"])

matches["year"] = matches["date"].dt.year

print(matches[["date","year"]].head())

print(matches[["result","win_type"]].head())

matches.to_csv("matches_cleaned.csv", index=False)

print("\nCleaned dataset saved successfully.")
```

---

## Output
<img width="1325" height="718" alt="image" src="https://github.com/user-attachments/assets/23da186d-232f-4480-9f50-86104cc24849" />
<img width="1322" height="727" alt="image" src="https://github.com/user-attachments/assets/ebc0af7b-3d25-403e-8069-6bc20dc7e32b" />
<img width="1312" height="730" alt="image" src="https://github.com/user-attachments/assets/424d756a-83f4-440d-9a91-794461eca01b" />
<img width="1313" height="722" alt="image" src="https://github.com/user-attachments/assets/ebbbfa8b-67be-4817-8a2e-275a9af565bd" />
<img width="1280" height="730" alt="image" src="https://github.com/user-attachments/assets/91b2ea07-9507-426c-b115-d2874894af65" />
<img width="1252" height="736" alt="image" src="https://github.com/user-attachments/assets/f27a8003-7229-4a50-8c8d-e6c7f7a9b561" />
<img width="1216" height="725" alt="image" src="https://github.com/user-attachments/assets/84e8591c-4ce4-434f-9fcf-8c81834419ed" />
<img width="1288" height="723" alt="image" src="https://github.com/user-attachments/assets/77cd4f73-fda4-4e3b-ab09-ea27d9496fd3" />
<img width="1317" height="728" alt="image" src="https://github.com/user-attachments/assets/8719a446-8bb8-4139-944d-a83dcfe8d116" />


## Result

The Exploratory Data Analysis (EDA) on the IPL matches dataset was successfully performed. Various visualizations were created to analyze seasonal trends, winning teams, toss decisions, and the stadiums hosting the highest number of matches.
