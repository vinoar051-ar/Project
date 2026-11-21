# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and teir top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here:

[2_Skill_Demand.ipynb](2_Skill_Demand.ipynb)

## Visualize Data

```python

fig, ax = plt.subplots(len(job_titles), 1)
sns.set_theme(style='ticks')
for i, job_title in enumerate(job_titles):

    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)

    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:r_r')

plt.tight_layout()
plt.show()

```

## Results

## Insights: Skill Demand in India Job Postings

### Overall
- **SQL and Python dominate all three roles** — they're the non-negotiable core of data careers in India
- Demand splits clearly by role: **analysts = reporting tools**, **engineers = pipelines/cloud**, **scientists = statistics/ML**
- Cloud (**AWS + Azure**) appears in both DE and DS but is **least important for analysts**

### Data Analyst
- **SQL is #1 (~52%)** — querying databases is the job
- **Python (~36%) ≈ Excel (~35%)** — Excel still nearly tied with Python; not obsolete here
- **Tableau (~27%) > Power BI (~21%)** — Tableau has the edge in postings (though Power BI is strong in enterprise India)
- **No cloud, no Spark** — this role is dashboards + queries, not infrastructure
- **Takeaway:** If targeting analyst roles: **SQL first, then Excel + a viz tool**, Python as accelerator

### Data Engineer
- **SQL nearly ~68%** — highest SQL demand of all three roles
- **Python ~61%** — strong second; scripting pipelines is core
- **Spark ~38%** — big-data processing is a real differentiator
- **AWS ~37% ≈ Azure ~36%** — dual-cloud market; neither wins decisively
- **Takeaway:** DE is the **highest-floor stack** (SQL + Python + Spark + cloud); hardest entry, clearest toolchain

### Data Scientist
- **Python ~70%** — #1 across the entire chart; DS is a Python-first role
- **SQL ~48%** — still essential, but secondary to Python (unlike DA/DE)
- **R ~33%** — only role where R matters meaningfully (stats/ML heritage)
- **AWS ~19% ≈ Tableau ~18%** — cloud and viz are nice-to-haves, not core
- **Takeaway:** DS = **Python + SQL + stats**; R helps for research-leaning posts; engineering skills less emphasized in job text

### Strategic implication (for your prep)
1. **Universal base:** SQL + Python — required everywhere
2. **Pick a lane:**
   - Analyst → + Excel, Tableau/Power BI
   - Engineer → + Spark, AWS/Azure
   - Scientist → + R/statistics, ML
3. **Don't over-invest in cloud for analyst roles** — postings rarely ask for it
4. **Power BI vs Tableau:** both appear, Tableau slightly higher in this dataset — check target companies before specializing
