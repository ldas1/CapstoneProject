# CapstoneProject
Final Semester Project. Restaurant order management system and customer order system.
# Cheat Day Catering Platform

DEPLOYED ON AWS AMPLIFY LINK: https://main.d3izqoj4p7aa12.amplifyapp.com/
## Overview
Cheat Day Catering Platform is a full-stack final semester project that focuses on building a **serverless web application** for a real-life sponsor. The system allows **customers** to browse the menu, place pickup orders, and view order information, while **employees** and **owners** can log in to manage and monitor orders. Payments are processed through **Stripe**, and the application is built on AWS using a serverless architecture. :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}

## Problem Statement
Many small catering businesses need a simple way to manage online orders, track order progress, and separate customer-facing functions from internal employee and owner operations. This project was created to provide a centralized ordering platform that supports:
- customer ordering and checkout
- internal order management
- owner analytics and oversight
- cloud-based deployment with scalable AWS services

## Core Features
### Customer Features
- Browse menu items with names, descriptions, and prices
- Add items to cart and manage quantities
- Enter billing information and place an order
- Pay securely using Stripe
- View order details after checkout through a customer-facing workflow

### Employee Features
- Log in through Amazon Cognito
- View incoming orders on the staff order management page
- Update order statuses such as Pending, Confirmed, In Prep, Ready, Completed, and Canceled

### Owner Features
- Log in with owner-level access through Amazon Cognito
- View owner revenue metrics and recent order data
- Access administrative functionality beyond employee permissions

These capabilities are reflected in the frontend role-based pages and backend routes for order creation, staff order retrieval, status updates, and owner revenue reporting. :contentReference[oaicite:2]{index=2} :contentReference[oaicite:3]{index=3} :contentReference[oaicite:4]{index=4}

## Technology Stack
### Frontend
- HTML
- CSS
- JavaScript
- AWS Amplify Hosting

### Backend
- AWS Lambda
- Amazon API Gateway
- Node.js

### Database
- Amazon RDS MySQL

### Authentication
- Amazon Cognito

### Payment Processing
- Stripe

### Monitoring / Operations
- Amazon CloudWatch

The architecture diagram for the project shows Amplify as the frontend host, API Gateway and Lambda as the backend layer, RDS as the database, Cognito for authentication, Stripe for payments, and GitHub as the source control and deployment source. :contentReference[oaicite:5]{index=5}

## Architecture
The system follows a serverless AWS architecture:

1. The frontend is hosted through **AWS Amplify**
2. Users interact with the web interface through the browser
3. API requests are sent to **Amazon API Gateway**
4. API Gateway triggers **AWS Lambda** functions
5. Lambda executes business logic and communicates with **Amazon RDS MySQL**
6. Staff and owner authentication is handled through **Amazon Cognito**
7. Payment processing is handled through **Stripe**

This architecture supports modularity, managed cloud services, and easier deployment across environments

## Major Backend Functions
The backend Lambda currently supports:
- **Owner revenue metrics** through `/owner/metrics/revenue`
- **Staff order retrieval** through `/staff/orders`
- **Order status updates** through `PATCH /staff/orders/...`
- **Order creation** through `POST /orders`

The order creation flow validates product pricing from the database, calculates tax, creates a Stripe payment intent, inserts customer data if needed, creates the order record, and stores the ordered products.

## Authentication and Role-Based Access
The application uses Amazon Cognito to separate internal access by role. Employees can access the staff order management page, while owners are granted broader access, including owner metrics and administrative functions. The frontend checks Cognito group membership to enforce authorized page access.

## Payment Handling
The system integrates with Stripe for payment processing. Stripe is used to create and confirm payment intents, which means sensitive card data is processed through Stripe rather than directly stored in the application backend. 

## Deployment
The frontend is designed to be deployed through **AWS Amplify**, connected to **GitHub** for version control and branch-based deployment. The backend runs in **AWS Lambda** behind **API Gateway**, and the system is intended to move through development, staging, and production environments. The architecture and deployment discussion for the project also support using Amplify for the public frontend and AWS services for the backend stack.

## Example User Flow
1. A customer visits the website
2. The customer browses the menu and adds items to the cart
3. The customer completes checkout and payment through Stripe
4. The order is created in the backend and stored in MySQL
5. Employees view the order on the staff dashboard
6. Employees update the order status
7. Owners can monitor the business using the owner dashboard and metrics page

The frontend cart and billing page, the staff orders page, and the owner metrics dashboard are all represented in the uploaded project files.
## Future Enhancements
Potential future improvements include:
- real-time customer order tracking
- dynamic menu management
- stronger production security hardening
- CI/CD pipeline improvements
- database backup and disaster recovery planning
- support for custom domains and production-ready sponsor deployment

## Educational Value
This project demonstrates how a real-world ordering platform can be built using a **serverless cloud architecture**. It combines frontend development, backend API design, database integration, authentication, payment processing, and cloud deployment into one complete system for a real-life sponsor.

## Author / Project Context
This project was developed as a **Final Semester Project** with the goal of creating a full serverless application that supports both customer-facing and internal business operations for a real sponsor.
