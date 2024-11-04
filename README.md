# jmeterLoadTest

## Overview

This repository contains a JMeter test plan designed for [insert purpose, e.g., performance testing an API, load testing a web application]. The test plan simulates multiple transaction scenarios, including deposits, money transfers, payments, and withdrawals.


## Table of Contents![jmeter](https://github.com/user-attachments/assets/9a81dca4-b788-404b-8ca4-2aa32dd4c6a9)


## Prerequisites

- **Apache JMeter**: [Download JMeter](https://jmeter.apache.org/download_jmeter.cgi)
- **Java Development Kit (JDK)**: [Download Link](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)

## Test Plan Structure

This JMeter test plan is designed to simulate multiple transaction scenarios as outlined below. Each thread group corresponds to a specific transaction type, with appropriate configurations to manage the load and simulate realistic user behavior.

### 1. Thread Groups

#### 1.1 Deposits
- **Purpose**: Simulates deposits performed by agents for customers.
- **Configuration**:
  - Number of Threads: 5 (agents)
  - Ramp-Up Time: 120 seconds
  - CSV Data Source: `deposit.csv` containing agent and customer IDs.
  
#### 1.2 Send Money
- **Purpose**: Represents money transfers from customers to other customers.
- **Configuration**:
  - Number of Threads: 5 (customers sending money)
  - Ramp-Up Time: 120 seconds
  - CSV Data Source: `sendMoney.csv` detailing sender and receiver customer IDs.

#### 1.3 Payments
- **Purpose**: Models payments made by customers to merchants.
- **Configuration**:
  - Number of Threads: 5 (customers making payments)
  - Ramp-Up Time: 120 seconds
  - CSV Data Source: `payment.csv` containing customer and merchant IDs.

#### 1.4 Withdrawals
- **Purpose**: Tests withdrawal scenarios using Boundary Value Analysis (BVA) for amounts.
- **Configuration**:
  - Number of Threads: [set number based on requirements]
  - Ramp-Up Time: 120 seconds
  - CSV Data Source: `withdraw.csv` containing withdrawal amounts calculated using BVA.

### 2. CSV Data Files

- **deposit.csv**: Contains columns for agent IDs and customer IDs.
- **sendMoney.csv**: Lists sender and receiver customer IDs for transactions.
- **payment.csv**: Contains customer IDs and merchant IDs for payment processing.
- **withdraw.csv**: Includes various withdrawal amounts for testing BVA scenarios.

### 3. HTTP Request Samplers

Each thread group contains HTTP Request Samplers configured to interact with the relevant API endpoints:
- **Deposits**: Sends POST requests to the deposit endpoint with agent and customer details.
- **Send Money**: Posts money transfer requests to the specified endpoint.
- **Payments**: Processes payment requests directed at merchant endpoints.
- **Withdrawals**: Executes withdrawal requests with amounts from the `withdraw.csv`.

### 4. Listeners

Listeners are included to monitor and analyze results:
- **View Results Tree**: For detailed request/response data.
- **Summary Report**: For an overview of performance metrics (e.g., response times, error rates).


