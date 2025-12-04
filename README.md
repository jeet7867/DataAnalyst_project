# The Analysis
 
## 1. what are the most demanded skills fir the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I finitered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlight the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here: [skill_count.ipynb](skills_count.ipynb)

### Visualize Data
```python
fig,ax =plt.subplots(len(job_titles),1)

sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
    df_plot=df_skills_perc[df_skills_perc['job_title_short']==job_title].head(5)
    sns.barplot(data=df_plot,x='skill_percent',y='job_skills',ax=ax[i],hue='skill_percent',palette='viridis')
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].get_legend().remove()
    ax[i].set_xlabel('Percentage (%)')
    ax[i].legend().set_visible(False)
    ax[i].set_xlim(0,80)

````
### Result
![Visualization of top skills](images/skill_demand_all_dataroles.png)

### Insight:

🔹 Data Analyst
```

SQL is the most in-demand skill (51%).

Excel remains a core requirement (41%).

Visualization tools like Tableau are moderately preferred (28%).

Python shows increasing relevance (27%).

SAS demand is comparatively low (19%).
```

🔹 Data Engineer
```

SQL (68%) and Python (65%) dominate the skillset.

Cloud technologies such as AWS and Azure show strong demand (32% each).

Big data framework Spark is equally important (32%).

Overall, Data Engineering roles emphasize backend, cloud, and large-scale systems.
````
🔹 Data Scientist
```
Python is the most required skill across all roles (72%).

SQL continues to be essential (51%).

R, SAS, and Tableau each hold moderate relevance (24%).

Demonstrates strong preference for programming and statistical tools.

```
 ## 🔍  Overall Trend Summary

SQL is universally required across all three roles.

Python dominates Data Engineer and Data Scientist roles.

Cloud + Big Data skills matter most for Data Engineers.

Analysts rely more on Excel and visualization tools like Tableau.
````
Skill demands reflect the differing focus of each role:

Analysts → Reporting & Visualization

Engineers → Data Infrastructure & Pipelines

Scientists → Modeling, ML, Experimentation
````

## 2. How are in-demand skills trending for Data Analysis?

### Visualize Data

```python
from matplotlib.ticker import PercentFormatter

sns.lineplot(data=df_DA_US_percent.iloc[:, :5],dashes=False,palette="tab10")
sns.set_theme(style='ticks')

plt.title('Trending Top Skills for Data Analysts in the US (%)')
plt.ylabel('Percentage of Job Posts (%)')   
plt.xlabel('')
plt.legend().remove()
sns.despine()
plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))
for i in range(5):
    plt.text(11, df_DA_US_percent.iloc[11, i] 
             , df_DA_US_percent.columns[i], color=sns.color_palette("tab10")[i])

plt.show()
```
### Results
![trending Top Skills for Data Analysts in the US](images/skills_trend.pngskills_trend.png)

*Line graph visualizng the trending top skills for data analyst in the US*


### Insight:
```

🔹 1. SQL remains the most in-demand skill

Consistently leads at 55–63% of all data analyst job postings.

Shows slight decline mid-year but maintains clear dominance.

Indicates SQL is a non-negotiable foundational skill.
```
```
🔸 2. Excel stays strong and stable

Second-most required skill at 34–45%.

Peaks around July–August, likely reflecting business reporting cycles.

Continues to be a core skill despite modern tools.
```
```
🟢 3. Tableau demand fluctuates

Moves between 28–36% across the year.

Slight surge during mid-year suggests increased hiring for BI/reporting roles.
```
```
🔴 4. Python demand shows a steady mid-year rise

Ranges from 28–34%.

Growth in June–July aligns with expanding need for automation and advanced analytics.

Closing months show renewed upward trend.
```
```
🟣 5. Power BI grows steadily throughout the year

Starts near 18% and rises towards 22–23%.

Slower but consistent adoption—reflecting Microsoft ecosystem expansion.
```