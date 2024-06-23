# Credit_Card_Financial_Analysis_Report
### To develop a comprehensive credit card weekly dashboard providing real-time insights into key performance metric and trends, enabling stakeholders to monitor and analyze credit card operations effectively
## DAX Queries Used:
Agegroup = SWITCH(
                TRUE(),
                'public cust_detail'[customer_age] < 30, "20-30",
                'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
                'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
                'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
                'public cust_detail'[customer_age] >= 60, "60+",
                )
Incomegroup = SWITCH(
                    TRUE(),
                    'public cust_detail'[income] < 35000, "Low",
                    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000, "Med",
                    'public cust_detail'[income] >= 70000, "High",
                    )
Week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
Current_week_revenue = CALCULATE(
                                SUM('public cc_detail'[revenue]),
                                FILTER(
                                ALL('public cc_detail'),
                                'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num_2])
                                )
                                )
Previous_week_revenue = CALCULATE(
                                SUM('public cc_detail'[revenue]),
                                FILTER(
                                ALL('public cc_detail'),
                                'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num_2])
                                -1)
                                )
