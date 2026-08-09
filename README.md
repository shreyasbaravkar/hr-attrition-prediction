# Employee Attrition Risk Prediction

## What is this project?

Companies lose good employees every year, and most of the time nobody sees it coming until the resignation letter is already on the table. This project tries to fix that — it looks at employee data and predicts **which employees are at risk of quitting**, and more importantly, **why** they might quit. The end result is an interactive dashboard that HR teams could actually use to act early instead of reacting late.

## The dataset

I used the **IBM HR Analytics Employee Attrition dataset** — 1,470 employees, 35 columns covering things like department, salary, job satisfaction, overtime, and whether they left the company or not.

## Tools I used

- **Python** (Google Colab) — for cleaning data, building the model, and explaining it
- **Pandas, Seaborn, Matplotlib** — for exploring and visualizing the data
- **Scikit-learn** — to build the prediction model
- **SHAP** — to explain *why* the model predicts what it predicts
- **Power BI** — to turn the results into an interactive dashboard

## How I approached it, step by step

**1. Looked at the raw data first.**
Before doing anything fancy, I just explored the data — how many employees left overall, which departments had the most attrition, whether overtime and income had any visible connection to people leaving. This step matters because you should never build a model on data you haven't looked at yet.

**2. Cleaned and prepared the data.**
Dropped a few columns that gave no useful information (like columns where every employee had the exact same value). Converted the target column (`Attrition`) from Yes/No into 1/0, since models only understand numbers. Converted other text columns (like Department, Job Role) into number columns the model can use — this is called **one-hot encoding**.

**3. Split the data and trained a model.**
Split the data into a training set (80%) and a test set (20%) — the model learns from the training set, and gets tested on data it has never seen, to check if it actually learned something real. I used **Logistic Regression**, a simple and well-understood model that's a great starting point for yes/no predictions like this.

**4. Handled the imbalance problem.**
Only about 16% of employees in this dataset actually left — so a lazy model could just predict "nobody leaves" and still look 84% accurate while being completely useless. I used class balancing to make sure the model actually pays attention to the employees who do leave, not just the majority who stay.

**5. Explained the model with SHAP.**
A prediction alone ("this person might quit") isn't very useful to HR — they need to know *why*. SHAP breaks down each prediction and shows which factors (overtime, low job satisfaction, income, etc.) pushed that specific employee's risk up or down. This turns a black-box model into something HR can actually act on.

**6. Built an interactive Power BI dashboard.**
Exported the model's predictions into a dashboard with:
- Top-line KPI cards (overall attrition rate, employees analyzed, average risk score)
- A chart showing which department has the highest risk
- A chart showing how job satisfaction relates to attrition risk
- A "Top 10 highest-risk employees" table, so HR has an actual action list, not just numbers
- Filters (slicers) for OverTime and Department, so anyone can drill down live

## What I found

- Overall predicted attrition rate: **[fill in your number, e.g. 33.7%]**
- The department with the highest attrition risk: **Sales**
- The biggest drivers of attrition, according to SHAP: **[fill in top 2-3 features from your SHAP chart, e.g. OverTime, low JobSatisfaction, low MonthlyIncome]**
- Model accuracy on the test set: **[fill in your number from Step 4]**

## The dashboard

<img width="1258" height="710" alt="Screenshot 2026-08-09 113317" src="https://github.com/user-attachments/assets/1074884b-7394-4079-bb12-0381d3f46f17" />
<img width="800" height="940" alt="image" src="https://github.com/user-attachments/assets/20bede0f-00db-4605-ab79-bf7daed58d8a" />




## What HR could actually do with this

Based on the findings, HR could prioritize reducing overtime and checking in on job satisfaction in high-risk departments like Sales, and use the "Top 10 at-risk employees" list as a starting point for real retention conversations — instead of finding out about a resignation after it's already decided.

## Why this project, not just another "I built a model" project

A lot of beginner projects stop at "I trained a model and got X% accuracy." This one goes one step further on both ends — it explains *why* the model thinks what it thinks (SHAP), and it turns the output into something a non-technical manager could actually open and use (Power BI dashboard) — not just a notebook only another data person could read.
