# Required Capstone Assignment 11.1: Draft the Problem Statement

**Course:** Professional Certificate in Machine Learning and Artificial Intelligence (UC Berkeley)
**Module:** Module 11, Practical Application 2
**Submitted:** on the course website (this file is a local copy of the submitted text)

---

## Overview

I want to understand whether customers with similar business profiles got similar discounts, or whether discounting is 
inconsistent across comparable customers. The domain is a SaaS business that offers products through monthly and yearly 
subscriptions, so the project will focus on identifying customers whose discount percentage is highly different than 
peers with similar revenue, tenure, and subscription characteristics.

## Data Needed

I would need customer-level subscription data such as monthly recurring revenue, discount amount, discount percentage, 
subscription plan and customer tenure. These fields would help compare peer groups and measure how each customer's 
discount differs from the expected discount for similar customers.

## Techniques

- Explore the data to compare discount distributions across different segments, revenue ranges, tenure and plans.
- Use clustering-based peer comparison, such as k-means, to group similar customers and calculate each customer's 
discount gap versus the peer-group average.
- Identify possible outliers or unusual discount profiles within each group, focusing on customers with much higher or 
lower discounts than similar customers.
