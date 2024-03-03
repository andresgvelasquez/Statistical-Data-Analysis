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