# 📊 IPL 2024 Analysis – Power BI Dashboard  

This repository contains a **comprehensive Power BI dashboard** analyzing the **IPL 2024 season**. The dashboard provides **deep insights** into team performances, toss impact, match outcomes, and key statistics using **interactive visualizations**.  

---

## 🚀 Features & Insights  
✅ **Total Matches Played** – Track the progress of the season.  
✅ **Team Performance (Wins & Losses)** – Compare teams based on match results.  
✅ **Toss Impact on Wins** – Analyze how winning the toss influences match outcomes.  
✅ **Match Wins by Decision Type** – Understand whether batting or fielding first leads to more victories.  
✅ **Total Runs & Wickets Analysis** – Identify top batting and bowling teams.  
✅ **Toss Win Impact Score** – Evaluate which teams benefit the most from winning the toss.  

---

## 📂 Contents  
📁 **Dashboard.pbix** – Power BI file with interactive visualizations.  
📁 **ipl2024_matches_cleaned.csv** – Raw IPL 2024 match data.  
📁 **Teams_Performance.xlsx** – Team-wise performance dataset.  
📁 **Presentation.pptx** – PowerPoint summarizing key insights.  
📁 **README.md** – Detailed documentation on the project.  

---

## 🛠 Tools & Technologies  
- **Power BI** for Data Visualization  
- **DAX (Data Analysis Expressions)** for calculations  
- **CSV / Excel** dataset for IPL 2024  

---

## 📊 Key DAX Formulas Used  

### **1️⃣ Total Matches Played**  
```DAX
Total_Matches = COUNT( 'ipl2024_matches_cleaned'[id] )

### **2️⃣ Total Wins by Team**  
```DAX
Total_Wins = 
COUNTROWS(
    FILTER( 'ipl2024_matches_cleaned', 
        'ipl2024_matches_cleaned'[winner] = SELECTEDVALUE(Teams_Performance[Team])
    )
)

### **3️⃣ Total Losses by Team**  
```DAX
Total_Losses = 
VAR TotalMatches = 
    COUNTROWS(
        FILTER('ipl2024_matches_cleaned', 
            'ipl2024_matches_cleaned'[team1] = SELECTEDVALUE(Teams_Performance[Team]) 
            || 'ipl2024_matches_cleaned'[team2] = SELECTEDVALUE(Teams_Performance[Team])
        )
    )

RETURN TotalMatches - [Total_Wins]


### **4️⃣ Toss Win Impact Score**  
```DAX
Toss_Win_Impact = 
DIVIDE(
    COUNTROWS(
        FILTER( 'ipl2024_matches_cleaned', 
            'ipl2024_matches_cleaned'[toss_winner] = 'ipl2024_matches_cleaned'[winner] 
        )
    ), 
    [Total_Matches], 
    0
)



🔍 How to Use

1️⃣ Clone the repository

git clone [https://github.com/your-repo-name.git](https://github.com/sharath1102/IPL-2024-Performance-Insights-using-Power-BI/)

2️⃣ Open Dashboard.pbix in Power BI

Load the dataset (ipl2024_matches_cleaned.csv & Teams_Performance.xlsx).

Refresh Power BI to update visuals.

Explore interactive charts, filters, and insights.

📢 Contribute & Feedback

We welcome contributions! 🚀

Feel free to open an issue if you find any problems.
Create a pull request for improvements.
🔗 Follow for more Power BI insights!

📌 Author: Sharath Yelle
📧 Contact: sharath.yellee@gmail.com


