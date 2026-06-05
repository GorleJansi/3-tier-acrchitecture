# 3-Tier Architecture

A 3-tier architecture separates an application into three logical layers:

1. Presentation tier
2. Application tier
3. Data tier

This separation makes the application easier to develop, deploy, scale, secure, monitor, and maintain.

## Example Application

Example: E-commerce application

An online shopping application like Amazon, Flipkart, or a small shopping website can be built using 3-tier architecture.

```text
User Browser / Mobile App
        |
        v
Presentation Tier
React website hosted on S3 + CloudFront
        |
        v
Application Tier
Node.js / Java Spring Boot APIs running on Kubernetes
        |
        v
Data Tier
PostgreSQL database + Redis cache + S3 storage
```

## 1. Presentation Tier

The presentation tier is the user-facing layer of the application.

This is what users interact with directly. It can be a website, mobile app, or desktop interface.

Examples:

```text
React frontend
Angular frontend
HTML/CSS/JavaScript website
Android/iOS mobile app
```

In an e-commerce application, this tier includes:

```text
Home page
Product listing page
Product details page
Shopping cart
Login page
Checkout page
```

The presentation tier sends user requests to the application tier. For example, when a user clicks "Add to Cart", the frontend sends a request to the backend API.

### DevOps Work In Presentation Tier

DevOps engineers help build, test, deploy, and monitor the frontend.

Typical DevOps tasks:

```text
Set up CI/CD pipeline for frontend code
Build frontend assets
Run linting and unit tests
Deploy static files to web servers or CDN
Configure domain and SSL certificates
Set up caching for faster page loading
Monitor frontend availability and performance
Manage environment variables
Handle rollback if a bad frontend release happens
```

Example tools:

```text
GitHub Actions
Jenkins
GitLab CI
Nginx
Apache
AWS S3
CloudFront
Netlify
Vercel
Docker
Kubernetes
```

Example DevOps flow:

```text
Developer pushes React code to GitHub
CI pipeline runs tests
Pipeline builds production files
Files are deployed to S3
CloudFront serves the website globally
Users access the frontend through HTTPS
```

## 2. Application Tier

The application tier is the business logic layer.

This tier processes user requests, applies business rules, communicates with the database, and returns responses to the presentation tier.

Examples:

```text
Node.js API
Java Spring Boot service
Python Django API
Python Flask API
.NET backend
Go microservice
```

In an e-commerce application, this tier handles:

```text
User login and authentication
Product search
Add to cart logic
Order placement
Payment processing
Inventory checks
Discount calculation
Sending emails or notifications
```

For example, when a user places an order, the application tier checks if the product is available, calculates the price, validates payment, creates the order, and stores order details in the database.

### DevOps Work In Application Tier

DevOps engineers are heavily involved in deploying and operating backend services.

Typical DevOps tasks:

```text
Create CI/CD pipeline for backend services
Build application artifacts or Docker images
Run unit tests, integration tests, and security scans
Deploy backend to servers, containers, or Kubernetes
Configure load balancers
Manage environment-specific configuration
Set up autoscaling
Manage secrets such as API keys and database passwords
Monitor logs, metrics, and traces
Configure health checks
Perform blue-green or rolling deployments
Handle rollback during failures
```

Example tools:

```text
Docker
Kubernetes
Helm
Jenkins
GitHub Actions
GitLab CI
AWS ECS
AWS EKS
AWS EC2
Terraform
Ansible
Prometheus
Grafana
ELK
OpenSearch
Vault
AWS Secrets Manager
```

Example DevOps flow:

```text
Developer pushes backend code
CI pipeline runs tests
Docker image is built
Image is pushed to container registry
Kubernetes deployment is updated
Pods are restarted with the new image
Load balancer routes traffic to healthy pods
Monitoring checks API response time and errors
```

## 3. Data Tier

The data tier stores and manages application data.

This tier usually contains databases, caches, file storage, and sometimes message queues.

Examples:

```text
MySQL
PostgreSQL
MongoDB
Redis
Amazon RDS
DynamoDB
Elasticsearch
S3 object storage
```

In an e-commerce application, this tier stores:

```text
User accounts
Product details
Orders
Payments
Cart data
Inventory data
Reviews
Session data
```

For example, when a user searches for a product, the application tier may query the database or search engine to return matching products.

### DevOps Work In Data Tier

DevOps engineers help make the data tier reliable, secure, backed up, and scalable.

Typical DevOps tasks:

```text
Provision databases using Infrastructure as Code
Configure database networking and access control
Set up automated backups
Test backup restoration
Configure replication and high availability
Monitor database performance
Set up alerts for CPU, memory, disk, connections, and slow queries
Manage database credentials securely
Apply database patches and upgrades
Support database migration pipelines
Configure encryption at rest and in transit
Plan disaster recovery
Scale databases vertically or horizontally
Manage cache services like Redis
```

Example tools:

```text
Terraform
Ansible
AWS RDS
Amazon Aurora
Azure SQL
Cosmos DB
PostgreSQL
MySQL
MongoDB Atlas
Redis
ElastiCache
Prometheus
Grafana
CloudWatch
Vault
Secrets Manager
Flyway
Liquibase
```

Example DevOps flow:

```text
Terraform creates an RDS PostgreSQL database
Database credentials are stored in Secrets Manager
Backend application reads credentials securely
Automated backups run daily
Read replica is configured for scaling reads
CloudWatch alarms monitor CPU and storage
Database migration runs during deployment
```

## Request Flow Example

When a user views a product:

```text
User clicks "View Product"
Frontend sends API request to backend
Backend checks product details from database
Backend returns product data
Frontend displays product page
```

When a user places an order:

```text
User clicks "Place Order"
Frontend sends order request
Backend validates user and cart
Backend checks inventory
Backend processes payment
Backend saves order in database
Backend sends response to frontend
Frontend shows order confirmation
```

## DevOps Responsibilities Across All Tiers

DevOps does not usually write the main business code, but DevOps ensures the application can be built, deployed, secured, monitored, scaled, and recovered properly.

Common DevOps responsibilities:

```text
CI/CD pipeline setup
Infrastructure provisioning
Cloud resource management
Containerization
Kubernetes deployment
Monitoring and alerting
Logging
Security scanning
Secret management
Backup and disaster recovery
Performance optimization
Cost optimization
Release management
Incident response
Automation
```

## Simple Mapping

```text
Presentation tier = User interface
Example = React website
DevOps work = Deploy frontend to CDN, configure SSL, cache static files

Application tier = Business logic
Example = Java Spring Boot API
DevOps work = Build Docker image, deploy to Kubernetes, configure autoscaling

Data tier = Data storage
Example = PostgreSQL database
DevOps work = Provision RDS, configure backups, monitoring, security, and replication
```

## Another Example: Banking Application

Presentation tier:

```text
Mobile banking app
Web banking portal
```

Application tier:

```text
Backend APIs for login
Balance check service
Money transfer service
Statement generation service
```

Data tier:

```text
Customer database
Transaction database
Audit logs
```

DevOps work:

```text
Presentation tier:
Deploy web portal, manage CDN, SSL, and frontend monitoring

Application tier:
Deploy secure backend APIs, manage scaling, logging, secrets, and compliance checks

Data tier:
Manage encrypted databases, backups, replication, disaster recovery, and access control
```

## Why 3-Tier Architecture Is Useful

Benefits:

```text
Better separation of responsibilities
Easier development and maintenance
Independent scaling of each tier
Improved security
Easier troubleshooting
Better deployment management
Higher availability
```

In short:

```text
Presentation tier = What the user sees
Application tier = Business logic
Data tier = Where data is stored

DevOps role = Automate, deploy, secure, monitor, scale, and recover each tier
```
