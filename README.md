# Credit_Card_Financial_Analysis_Report
### To develop a comprehensive credit card weekly dashboard providing real-time insights into key performance metric and trends, enabling stakeholders to monitor and analyze credit card operations effectively
## DAX Queries Used:
### Age_group= SWITCH(
                TRUE(),
                'public cust_detail'[customer_age] < 30, "20-30",
                'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
                'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
                'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
                'public cust_detail'[customer_age] >= 60, "60+",
                )
