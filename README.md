# Megaline: What's the Best Plan?

## Contact
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/andres946/)
[![Correo Electrónico](https://img.shields.io/badge/Correo%20Electrónico-andresgvelasquez8@gmail.com-red?style=for-the-badge&logo=mail.ru)](mailto:andresgvelasquez8@gmail.com)  

## Description:
This project aims to analyze the behavior of Megaline's customers. The company offers its customers two prepaid plans, Surf and Ultimate. The sales department wants to know which of the plans generates more revenue in order to adjust the advertising budget.

A preliminary analysis of the plans will be conducted based on a relatively small selection of customers. Data from 500 Megaline customers is available: who the customers are, where they are from, which plan they use, as well as the number of calls they made and the text messages they sent in 2018. Your task is to analyze customer behavior and determine which prepaid plan generates more revenue.

## Description of the Plans:

**Note:** Megaline rounds seconds to minutes and megabytes to gigabytes. For calls, each individual call is rounded up: even if the call lasted only one second, it will be counted as one minute. For web traffic, individual web sessions are not rounded up. Instead, the total for the month is rounded up. If someone uses 1025 megabytes this month, they will be charged for 2 gigabytes.

Below is a description of the plans:

**Surf**

1. Monthly payment: $20.
2. 500 minutes per month, 50 SMS, and 15 GB of data.
3. If the package limits are exceeded:
    - 1 minute: $0.03.
    - 1 SMS: $0.03.
    - 1 GB of data: $10.

**Ultimate**

1. Monthly payment: $70.
2. 3000 minutes per month, 1000 SMS, and 30 GB of data.
3. If the package limits are exceeded:
    - 1 minute: $0.01.
    - 1 SMS: $0.01.
    - 1 GB of data: $7.

## Data Dictionary:

1. **users** table (user data):
 
- *user_id*: unique user identifier.
- *first_name*: user's first name.
- *last_name*: user's last name.
- *age*: user's age (in years).
- *reg_date*: subscription date (dd, mm, yy).
- *churn_date*: date when the user stopped using the service (if absent, the tariff was in use when this database was extracted).
- *city*: user's city of residence.
- *plan*: tariff name.

2. **calls** table (call data):
 
- *id*: unique call identifier.
- *call_date*: call date.
- *duration*: call duration (in minutes).
- *user_id*: user identifier who made the call.

3. **messages** table (SMS data):
 
- *id*: unique SMS identifier.
- *message_date*: SMS date.
- *user_id*: user identifier who sent the SMS.

4. **internet** table (web session data):
 
- *id*: unique session identifier.
- *mb_used*: volume of data used during the session (in megabytes).
- *session_date*: web session date.
- *user_id*: user identifier.

5. **plans** table (tariff data):
 
- *plan_name*: tariff name.
- *usd_monthly_fee*: monthly payment in US dollars.
- *minutes_included*: included minutes per month.
- *messages_included*: included SMS per month.
- *mb_per_month_included*: included data per month (in megabytes).
- *usd_per_minute*: price per minute after exceeding package limits (for example, if the package includes 100 minutes, the operator will charge for minute 101).
- *usd_per_message*: price per SMS after exceeding package limits.
- *usd_per_gb*: price per gigabyte of extra data after exceeding package limits (1 GB = 1024 megabytes).

## Virtual Environment Setup

To run this project, it is recommended to create a Python virtual environment. You can do this by executing the following commands in your terminal:

```bash
python -m venv venv
source venv/bin/activate  # For Linux/Mac
# or
.\venv\Scripts\activate   # For Windows
```

Then, you need to install the dependencies:

```bash
pip install -r requirements.txt
```
Once you have set up the virtual environment and installed the dependencies, you can run the project.

## Conclusions

**Hypothesis Testing**
1. After conducting a t-test, it was found that there is a significant difference in the average revenue from users between different call plans. Therefore, the null hypothesis, which states that the average revenue from users of the call plans is the same, is rejected.

2. However, when comparing the average revenue of users in the NY-NJ area with that of users in other regions using a t-test, there was not enough evidence to reject the null hypothesis. This suggests that there are likely differences in the average revenue between the NY-NJ region and the rest of the regions.

### **User Behavior**

**Income**

- The average revenue for the Surf plan is $60.70 USD, while for the Ultimate plan it is $72.31 USD. This suggests that Ultimate plan users, on average, only pay the monthly fee, whereas Surf plan users tend to pay more due to exceeding service limits, nearly three times the monthly fee. Nevertheless, the average price of the Surf plan is still lower than that of the Ultimate plan.

- The standard deviation for the Surf plan is $55.38 USD, whereas for the Ultimate plan it is $11.39 USD. Values are less dispersed in the Surf plan. Ultimate plan users tend to be more consistent in their monthly spending.

- 75% of Ultimate plan users spend $70 USD (only the monthly fee), while 25% of Surf plan users spend $20 USD (only the monthly fee).

- There is a 25% of users in the Surf plan who spend more than the equivalent of the monthly fee for the Ultimate plan ($70 USD).

- The maximum spending for Surf plan is $590.37 USD compared to the Ultimate plan's maximum of $182 USD. Surf plan users tend to spend more.

**Internet Consumption**  

The behavior varies according to the plan.

- The mean for Surf is 14.59 GB and for Ultimate is 16.34 GB.
- Users with the Ultimate plan tend to use fewer megabytes in total per month until February, after which Surf plan users consume more gigabytes (due to there being more Surf plan users than Ultimate plan users).
- On average, Surf plan users consume slightly more gigabytes in the months of June and July. The Ultimate plan surpasses in other months. For February, March, and April, there is a significant difference of approximately 20% more than the Surf plan.
- The distribution of both plans exhibits a right-skewed behavior (the upper whisker of the boxplot is longer than the lower one).
- No outliers are observed.

**Messages**

The behavior varies according to the plan.

- Both datasets for the two plans exhibit right-skewed data.
- The mean for Ultimate is 2285 messages and for Surf is 4051 messages.
- Users with the Ultimate plan tend to use fewer messages in total until March, after which Surf plan users start sending messages (simply because there are twice as many Surf plan users as Ultimate plan users).
- Analyzing the average number of messages per plan, it was found that Surf plan users send more messages on average per month for all months, ranging from 15% to 80% larger compared to the Ultimate plan average.
- The distribution of both plans exhibits right-skewed behavior (the upper whisker of the boxplot is longer than the lower one).
- It appears that the Surf plan has more dispersion of values, as indicated by the longer whiskers.
- No outliers are observed.
- The demand for messages increases each month. In December, the demand for messages in the Surf plan is almost double that of the Ultimate plan.


**Calls**

User behavior clearly varies according to the plan.

- Users with the Ultimate plan tend to use fewer minutes in total until February, after which Surf plan users consume more minutes. This occurs because the number of Surf plan users is approximately twice that of the Ultimate plan.

- Analyzing the average minutes per month per plan:
    1. Surf plan is slightly higher in the months: January, March, April, June, July, and December.
    2. Ultimate plan is superior (25% higher) than Surf plan in February and slightly higher in other months.

- The distribution of both plans exhibits right-skewed behavior (the upper whisker of the boxplot is longer than the lower one).

- The mean of the Surf plan in call minutes is around 56,000, while for the Ultimate plan it is around 25,000.

- It appears that the Surf plan has more dispersion of values, as indicated by the longer whiskers.

- No outliers are observed.

- As the months pass, the demand increases. By December, the difference in demand is almost double, with the Surf plan being the highest consumer (due to the existence of more Surf plan users).
