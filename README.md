# Product Price Comparison Application

A microservices-based application that allows users to compare product prices from different dealers. This project demonstrates how to build and deploy multiple microservices that work together as a complete application on IBM Cloud Code Engine.

## Table of Contents
- [Overview](#overview)
- [Architecture](#architecture)
- [Features](#features)
- [Screenshots](#screenshots)
- [Deployment Steps](#deployment-steps)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Lessons Learned](#lesson-learned)

## Overview

This application helps users find the best price for products by comparing offerings from multiple dealers. Users can select a product, view available dealers, and compare pricing to make informed purchasing decisions.

## Architecture

This application uses a microservices architecture with three main components:

1. **Product Details Service (Python)** - Provides product information
2. **Dealer Pricing Service (Node.js)** - Provides dealer pricing information
3. **Frontend Service (HTML/JavaScript)** - Provides the user interface

## Features

- Display a list of available products
- Show dealers that supply a selected product
- Display pricing information for a selected dealer
- Compare prices across all dealers for a product
- Responsive user interface

## Screenshots
![Screenshot 2025-04-06 210006](https://github.com/user-attachments/assets/5face3ac-a8fe-4c02-9473-dd569f5ab75a)

## Deployment Steps

### 1. Deploy the Product Details Microservice

```bash
ibmcloud ce application create --name prodlist --image us.icr.io/${SN_ICR_NAMESPACE}/prodlist --registry-secret icr-secret --port 5000 --build-context-dir products_list --build-source https://github.com/ibm-developer-skills-network/dealer_evaluation_backend.git
```

### 2. Deploy the Dealer Pricing Microservice

```bash
ibmcloud ce application create --name dealerdetails --image us.icr.io/${SN_ICR_NAMESPACE}/dealerdetails --registry-secret icr-secret --port 8080 --build-context-dir dealer_details --build-source https://github.com/ibm-developer-skills-network/dealer_evaluation_backend.git
```

### 3. Configure and Deploy the Frontend Microservice

```bash
# Clone the repository
git clone https://github.com/ibm-developer-skills-network/dealer_evaluation_frontend.git

# Update the index.html file with deployment URLs

# Deploy the frontend
ibmcloud ce application create --name frontend --image us.icr.io/${SN_ICR_NAMESPACE}/frontend --registry-secret icr-secret --port 5001 --build-source .
```

## Technologies Used

- **Backend**:
  - Python (Product Details Service)
  - Node.js (Dealer Pricing Service)
  - REST APIs
  
- **Frontend**:
  - HTML
  - JavaScript
  - CSS
  
- **Cloud Services**:
  - IBM Cloud Code Engine
  - IBM Container Registry

## Lessons Learned

- Microservices architecture allows for independent development and deployment of components
- Cloud deployment provides scalability and availability benefits
- Cross-service communication requires careful URL configuration
- Different programming languages can be used for different services based on requirements
