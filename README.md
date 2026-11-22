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

![Visualization of Top Skills for Data Nerds](images/skill_demand_all_data_roles.png)

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

## 2. How are in-demand skills trending for Data Analysts?

### Visualize Data

```python

df_plot = df_DA_IND_percent.iloc[:, :5]

sns.lineplot(data=df_plot, dashes=False, palette='tab10')
sns.set_theme(style='ticks')
sns.despine()

plt.title('Trending Top Skills for Data Analysts in India')
plt.ylabel('Likelihood in Job posting')
plt.xlabel('')
plt.legend().remove()
for i in range(5):
    plt.text(11.2, df_plot.iloc[-1,i], df_plot.columns[i])

from matplotlib.ticker import PercentFormatter

ax = plt.gca()

ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()

```

### Results
![Trending Top skills for Data Analysts in India](images\skill_trend_DA.png)
*Bar graph visualizing the trending top skills for data analysts in India*

## Insights: Trending Top Skills for Data Analysts in India

### Overall
- **SQL never drops below ~52%** — it's the one constant; every other skill is a distant, volatile second tier
- **May is the spike month** — SQL hits ~69%, Excel jumps to ~58%, Tableau/Power BI also peak: seasonal hiring burst
- **Power BI has the strongest growth story** — from ~18% (Jan) to ~34% (Dec), nearly doubling; the only clear long-term riser
- Demand is **bumpy, not smooth** — mid-year (Jun–Sep) cools for most skills, then **Q4 (Oct–Dec) recovers**

### Skill-by-skill
- **SQL:** 52% → 69% (May) → ends ~62%. Always #1; the May–June swing (~15 pts) is the biggest single move on the chart
- **Python:** dips hard in **Mar (~26%)**, recovers to ~45% (Jun), ends ~44%. Closely tracks Excel — they trade 2nd/3rd place all year
- **Excel:** dramatic **May spike to ~58%** (from ~35% in Apr), settles back to ~40%. Proof Excel is still very alive in Indian DA hiring
- **Tableau:** stable band **~28–37%**, peaks May/Oct/Dec. Mature, steady demand — no breakout, no collapse
- **Power BI:** lowest all year but **steadiest climber** — ~18% → ~34%, with an Aug bump (~30%) and strong Dec finish

### What this means (prep takeaways)
1. **SQL is non-negotiable** — if you only go deep on one thing, it's this
2. **Python + Excel together** still beat any single viz tool for DA roles in India
3. **Power BI is the skill to add in 2026** — momentum is upward; Tableau is flat-to-stable
4. **Plan applications around May and Q4** — posting volume (and skill mentions) peak then; Mar is the coolest month for Python-heavy DA posts
5. **Don't panic at mid-year dips** — Jun–Sep dips look seasonal across almost every skill, not a demand crash

