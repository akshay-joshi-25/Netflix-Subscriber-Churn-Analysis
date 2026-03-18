# 📊 **Netflix Subscriber Churn Analysis**

This project serves two objectives:
1. Analyze which metrics are statistically impacting the churn rate of Netflix subscriptions.
2. Predict the churn rate of future customers using a Random Forest.

# 📌 **Overview**

This project will cover the following:
- Conduct a high-level analysis of Netflix's subscribers for the years 2022 and 2023.
- Perform statistical tests to identify which variables impact the churn rate of Netflix's subscribers.
- Build a Random Forest based on data for the years 2022 and 2023.
- Use the Random Forest to predict the churn rate for 2024 subscribers data.

# 📂 **Datasets**
The dataset used for this project were publicly made available by Fatolu Peter on Kaggle. It contained data for the period between Jan 1, 2022 and June 19, 2024.

You can access the dataset by clicking [here](https://www.kaggle.com/datasets/olagokeblissman/netflix-user-behavior-and-subscription-dataset/data).

# 🔧 **Tools Used**

- **Python** was used for statistical analysis and building a random forest.
- **Excel** was used for data visualization and exploratory data analysis.

# 🧾 **Data Table**

The Netflix Churn Dataset contained 50,000 records and 29 variables belonging to the following categories:

### **User Demographics**
- **user_id** - Unique Identifier for each user.
- **age_group** - Age of the user in years.
- **gender** - Gender of the user.
- **country** - Country where the user is located.
- **region** - Broader geographic region.

### **Subscription Details**
- **subscription_plan** - The tier of Netflix plan the user is subscribed to.
- **monthly_fee** - Monthly fee charged to the user in USD.
- **subscription_start_date** - Date when the user first subscribed.
- **subscription_end_date** - Date when the subscription ended or is due to end.
- **payment_method** - Method used to pay for the subscription.
- **discount_applied** - Whether a discount was applied to the subscription.

### **Target Variable**
- **churn_status** - Whether the user has cancelled their subscription.

### **Content Watched**
- **title** - Title of the content watched.
- **content_type** - Whether the content is a movie or a series.
- **genre** - Genre of the content.
- **language** - Language of the content.
- **release_year** - Year the content was originally released.

### **User Engagement**
- **device_type** - Device used to watch content
- **watch_time_minutes** - Total minutes watched in the recorded session
- **session_count** - Number of sessions recorded for the user
- **completion_percentage** - Percentage of the content completed during the session
- **date_watched** - Date the content was watched
- **time_of_day** - Time of day the content was watched
- **rating** - User rating given to the content (1–5 scale)
- **liked** - Whether the user liked the content
- **recommendation_source** - How the user discovered the content
- **days_since_last_watch** - Number of days since the user last watched any content
- **avg_weekly_watch_time** - Average number of minutes watched per week
- **content_diversity_score** - Score (0–1) reflecting how varied the user's content consumption is across genres and types

# 📈 **High-Level Analysis**

<img width="623" height="391" alt="image" src="https://github.com/user-attachments/assets/715abef7-8836-49cc-be9f-0f605643536b" />

Overall subscriber volume stayed nearly flat — both years sit just above 20K total subscribers, meaning the platform neither grew nor lost its user base meaningfully between 2022 and 2023. The churn rate increased by 0.4 percentage points year-over-year. While that sounds small, on a ~20K base it represents roughly 80 additional users who cancelled compared to the prior year.

These observations indicate that:
- **Retention is holding, but softening.** The platform kept ~83% of its users both years, which is a reasonably strong retention rate, but the downward drift suggests the pressure to cancel is gradually increasing.
- **Growth is stagnant.** If total subscribers are flat while some users are churning, it means new subscriber acquisition is just about offsetting cancellations — the platform is running to stand still.
- **The churn problem is not improving on its own.** Without an intervention — whether that's improving engagement, adjusting pricing, or upgrading Basic plan users — the 2024 figure would likely continue drifting toward 18% and beyond based on this trend.

# 🧮 **Metrics Impacting Churn Rate - Statistical Analysis**

Two tests were used to identify which variables significantly affect churn:
- Chi-Square test for categorical variables (p < 0.05 = significant)
- Independent samples T-test for numeric variables (p < 0.05 = significant)

<img width="1183" height="698" alt="image" src="https://github.com/user-attachments/assets/480bfc7e-1c77-4104-947c-fbb51ffe94ac" />


The above results clearly demostrated that subscription_plan is the only categorical variable that significantly affects churn (p = 0.00).
Basic plan users churn at 25.4%, more than triple the Premium rate of 7.6%, with Standard sitting at 14.9%. Plan tier is the strongest categorical predictor of churn in the dataset.

All remaining categorical variables returned p-values well above 0.05, meaning their churn rate differences across categories are likely due to random chance rather than a real effect

<img width="1188" height="376" alt="image" src="https://github.com/user-attachments/assets/192da44c-94ac-4ca0-b670-d12a1d795008" />

The above results clearly demonstrated that FOUR variables - watch_time_minutes, session_count, completion_percentage, and avg_weekly_watch_time significantly impact churn (p = 0.00). This indicates that users who watch less, watch less often, and complete less content are significantly more likely to cancel.

**Key Takeaway:** Only five variables are statistically significant predictors of churn: subscription_plan, watch_time_minutes, session_count, completion_percentage, and avg_weekly_watch_time. Everything else — demographics, payment method, device, region, discounts — shows no statistically meaningful relationship with churn at the 95% confidence level.

# 🧠 **2024 Netflix Subscribers Churn Prediction - Random Forest**

### **Random Forest Feature Importance**
Feature importance measures each variable's proportional share of the total Gini impurity reduction across all 100 decision trees. A higher percentage means the model relied on that variable more heavily when learning to separate churned from active users. All 18 values sum to 100%.

<img width="648" height="628" alt="image" src="https://github.com/user-attachments/assets/d2c559ae-7a2d-452c-b055-cdcc82cf680d" />

The above results showed that FOUR variables - avg_weekly_watch_time, content_diversity_score, days_since_last_watch, and watch_time_minutes collectively account for over 50% of the model's predictive power. The model is essentially saying: how much someone watches, how varied their viewing is, how recently they watched, and how long each session lasts are the strongest behavioural signals of churn risk.

**Key Takeaway:** The Random Forest reinforces the same conclusion as the statistical tests: churn is a behavioural problem, not a demographic one.

### **Predicting using the Random Forest**
