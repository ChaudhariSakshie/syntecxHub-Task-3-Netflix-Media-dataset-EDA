# Netflix / Media Dataset – Exploratory Data Analysis (EDA)

**Internship:** Syntecx Hub (Data Science)

**Candidate:** Sakshi Vijay Chaudhari  
**College:** Jayawantrao Sawant College of Engineering, Pune


## 1. Objective
The objective of this project is to perform Exploratory Data Analysis (EDA) on a Netflix / Media dataset to understand content distribution, growth trends over time, popular genres, runtime characteristics, and generate top-10 analytical summaries. The project concludes with visual insights and a concise analytical summary suitable for internship evaluation.


## 2. Dataset Description
- Dataset: Netflix Movies and TV Shows dataset (`netflix_titles.csv`)
- Records: Movies and TV Shows available on Netflix
- Key Columns Used:
  - `type` (Movie / TV Show)
  - `release_year`
  - `duration`
  - `listed_in` (Genres)


## 3. Tools & Libraries Used
- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## 4. Data Loading & Inspection
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv('netflix_titles.csv')

# Preview data
df.head()
```

---

## 5. Data Cleaning
- Removed missing values from important columns
- Extracted numeric values from duration

```python
df = df.dropna(subset=['type', 'release_year', 'listed_in', 'duration'])

df['duration_value'] = df['duration'].str.extract('(\d+)').astype(int)
```

---

## 6. Content Distribution by Type
```python
type_counts = df['type'].value_counts()

type_counts.plot(kind='bar')
plt.title('Distribution of Content by Type')
plt.xlabel('Type')
plt.ylabel('Count')
plt.show()
```

**Observation:** Movies dominate the Netflix content library compared to TV Shows.

---

## 7. Content Growth Over Time
```python
yearly_content = df.groupby('release_year').size()

yearly_content.plot(figsize=(12,5))
plt.title('Netflix Content Growth Over Years')
plt.xlabel('Release Year')
plt.ylabel('Number of Titles')
plt.show()
```

**Observation:** Netflix shows rapid growth in content after 2012, peaking during the late 2010s.

---

## 8. Genre Analysis
```python
genres = df['listed_in'].str.split(', ').explode()
genre_counts = genres.value_counts()

genre_counts.head(10).plot(kind='barh')
plt.title('Top 10 Genres on Netflix')
plt.xlabel('Count')
plt.ylabel('Genre')
plt.show()
```

**Observation:** Drama and Comedy are the most common genres on Netflix.

---

## 9. Runtime Distribution
### Movies
```python
movies = df[df['type'] == 'Movie']
movies['duration_value'].plot(kind='hist', bins=30)
plt.title('Movie Runtime Distribution')
plt.xlabel('Duration (Minutes)')
plt.show()
```

### TV Shows
```python
tv_shows = df[df['type'] == 'TV Show']
tv_shows['duration_value'].plot(kind='hist', bins=10)
plt.title('TV Show Seasons Distribution')
plt.xlabel('Number of Seasons')
plt.show()
```

---

## 10. Top‑10 Analysis
### Top 10 Genres
```python
genre_counts.head(10)
```

### Top 10 Release Years
```python
yearly_content.sort_values(ascending=False).head(10)
```

---

## 11. Key Insights Summary
- Movies form the majority of Netflix’s catalog.
- Content production increased significantly after 2012.
- Drama and Comedy are the most prevalent genres.
- Most movies fall within 80–120 minutes runtime.
- TV shows are generally limited to 1–3 seasons.

---

## 12. Conclusion
This EDA provides meaningful insights into Netflix’s content strategy and trends. The visualizations and statistical summaries help understand user‑oriented content patterns and platform growth. This project demonstrates practical data analysis, visualization, and interpretation skills aligned with the ShadowFox Data Science Internship requirements.

---

## 13. References
- Netflix Dataset (Kaggle)
- YouTube Tutorials used for reference

