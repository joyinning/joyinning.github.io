---
title: Gym Management System 
date: 2024-04-29
categories: [Projects, Cloud Management] 
tags: [Data Engineering, Cloud Management, Business Intelligence Engineering, Azure Cloud Service, Fitness Industry]
pin: true
---

[![Open in Github Page](https://img.shields.io/badge/Hosted_with-GitHub_Pages-blue?logo=github&logoColor=white)](https://github.com/joyinning/gym_management_system_cloud_service)

# Gym Management System 
## PART 1 Project Overview
**Background and Project Goal**
1. The Global Health and Fitness industry is expected to grow significantly by 2030, with a notable increase in interest from Gen Z, making it an attractive sector for investment.
2. The introduction of a cloud-based gym management system using Azure Cloud Services has significantly enhanced operational efficiency and customer satisfaction by providing streamlined access to crucial data and operational tools.
3. The project aims to build a comprehensive application for gym management that utilizes Azure's technologies to enhance database management, operation support, and business performance analysis.

**Cloud Services Used in the Project**
1. **Azure Database/SQL Server** was used to create a scalable and secure database infrastructure that supports various aspects of gym management including enrollment, wellness management, and workout tracking.
2. **Azure IAM** was implemented to ensure that only authorized personnel can access certain data and functionalities, enhancing security and operational efficiency.
3. **Power BI** was integrated with Azure to manage and visualize complex datasets, facilitating data-driven decision-making regarding operational performance, member engagement, and financial health.
4. **ASP.NET** was used to develop a webpage for managing employees within the database system.

## PART 2 Azure SQL Server/Database
Explore and analyze the given dataset through the following methods to select the best features for better performance of machine learning models. We will conduct the following strategies.

1. **Create SQL Database and Server**: The initial setup involved creating an SQL database and server in Azure, focusing on cost-effectiveness, scalability, storage flexibility, and ensuring connectivity with other Azure services. <br><img width="616" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/eb8f689e-57b9-4350-bfc3-966e02bb3d95">

2. **Azure Data Studio**: Azure Data Studio was used to connect to the SQL server, authenticate using SQL login, and begin creating tables within the database.<br> <img width="396" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/5a6374bb-422b-4abd-a835-6dc565b12449">

3. **Build the Structure of the Database - People**: An Entity-Relationship Diagram (ERD) was developed for the "People" component of the gym management system, detailing tables for employees, managers, departments, and various logs concerning members, their health metrics, fitness goals, and activities. <img width="679" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/48e9e23d-55cf-4fc1-a325-815bdd361d05">

4. **Build the Structure of the Database - Equipment**: The "Equipment" section of the database tracks all gym equipment details, maintenance records, reservations, and usage data, structured around an ERD.<img width="684" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/6476c714-bc37-42c7-a6f1-d32f33baa80b">

5. **Build the Structure of the Database - Payments**: The "Payments" section records detailed financial transactions, pricing changes, and coupon data, facilitating comprehensive financial management and reporting.<img width="690" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/84858b99-648f-4b4b-8b36-9dee8b104624">

6. **Generate Random Values**: Due to the absence of a relevant pre-existing dataset, random data values were generated and incorporated into the database tables to simulate realistic data during the development and testing phases.<img width="250" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/3e86b463-fb39-402f-a150-f7609069335f"> <img width="250" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/747af283-da67-43aa-8532-3f954e1c788e"> <img width="250" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/51109319-48ab-4e77-9ba8-aa003f605dca">

## PART 3 Web Application Development and Power BI Integration
1. **ASP.NET Web Application Development**: This project segment involves creating an ASP.NET web application to facilitate the management of a gym's database, focusing primarily on customer and employee data. The web application is designed to allow non-technical staff to perform CRUD (Create, Read, Update, Delete) operations easily on customer and employee information. <img width="630" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/efeb7792-bb45-42bf-8be6-0c8f33c27f50">
2. **Power BI Integration**: The application includes Power BI dashboards tailored to the gym management's needs, enhancing operational efficiency by focusing on key performance indicators. These dashboards provide real-time insights into various aspects of gym management.
  - **Financial Dashboard**: Tracks financial health by monitoring metrics like monthly revenue, transaction volumes, and customer spending behaviors. 
  - **Equipment and Maintenance Dashboard**: Offers insights into gym equipment status and maintenance needs to optimize operational performance. <img width="640" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/528e6789-6a4f-40f8-a355-937fe383610d">
  
  - **Member Health Metrics and Goal Management Dashboards**: These visualizations show health trends and workout progress, helping tailor gym programs to member needs.<img width="631" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/cfff70fe-69b7-4cd2-aa5f-0924bc6c370e">

  - **Course Metrics and Member Registration Dashboards**: Analyze course popularity and member registration trends to improve planning and marketing strategies. <img width="645" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/8a01ceb2-c8d0-4e72-956e-17b8b9195dc6">

## PART 4 Cost Management
Upon deployment of our Azure database, we initiated a detailed analysis of both data storage and CPU utilization to ensure that we were aligning with budget constraints and performance targets.
<br>
<br>
**Database Data Storage and CPU Usage**<bR>
<img width="620" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/03f34d9d-cf49-49eb-a778-3f87dc2dc7e8">

1. **Database Data Storage**: Initially, the data storage utilization was commendably low at only 0.15% of the total capacity, which not only showcases the efficiency of our storage management but also confirms ample room for scaling up operations as demand increases.
2. **CPU Usage During Development**: While the storage metrics were within acceptable limits, CPU usage presented a challenge. During the database setup phase, which included creating tables and populating them with data via T-SQL scripts, CPU usage on the SQL instance spiked to 61%. This was identified during a process where 27 tables were being populated simultaneously.
3. Strategies for Optimization:
  - **Sequential Processing**: To mitigate high CPU usage, we adjusted our strategy by breaking down the task of table creation and data insertion into multiple sequential steps rather than executing them simultaneously. This approach significantly reduced CPU stress and resulted in a more balanced utilization.
  - **Performance Monitoring Tools**: Implementing tools to continuously monitor CPU and memory usage during heavy operations helped in proactively managing potential overloads.
CPU and SQL Instance Usage After Connecting to Power BI

**CPU and SQL Instance Usage After Connecting to Power BI**<br>
<img width="419" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/1fbb6b4d-4a70-4fc2-ace8-812e5a9ca8c8">

1. **Database Data Storage**: The integration of Power BI for real-time data analytics initially employed the DirectQuery method. This setup led to a CPU usage of 60%, which, while providing up-to-the-minute data updates, proved to be costly in terms of resource utilization.
2. Strategies for Optimization:
  - **Switch to 'Import' Mode in Power BI**: Recognizing the high cost and resource demand of DirectQuery, we transitioned to using the 'Import' mode in Power BI. This method involves importing data into Power BI's memory, which is refreshed at predefined intervals instead of querying the database in real-time. This change significantly reduced the CPU load and associated operational costs.
  - **Optimizing Refresh Schedules**: To further enhance efficiency, we optimized the data refresh schedules in Power BI to times of low activity on the SQL instance, thus ensuring minimal impact on the performance of our operational systems.

## PART 5 Future Improvements/Activities
**Customer Analysis**
1. Targeting Generation Z: Develop targeted marketing strategies that resonate with Generation Z by utilizing the gym's comprehensive database to understand their fitness preferences and lifestyles.
2. Personalized Campaigns: Create personalized marketing initiatives tailored to Generation Z’s values and preferences to boost engagement and loyalty.
3. AI and Machine Learning Models: Implement AI or machine learning models to track and manage health metrics, goals, and workout logs of Generation Z members.

**Business Analytics and Development**
1. Predictive Analytics: Use advanced analytics to predict future fitness trends and demographic shifts to strategically tailor gym offerings.
2. Expansion Planning: Analyze data from successful locations and demographic trends to make informed decisions on new market expansions.

**Cloud and Database Management**
1. Enhanced Security: Strengthen security measures to protect sensitive member information effectively.
2. Database Optimization: Optimize the scalability and performance of the database to support the gym's growing needs and innovation strategies.
