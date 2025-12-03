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

### Insight

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