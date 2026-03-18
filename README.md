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

The Netflix Churn Dataset contains the following type of variables:

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
