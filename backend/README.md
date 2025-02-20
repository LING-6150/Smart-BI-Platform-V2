This is a Spring Boot project starter template, which integrates commonly used frameworks and provides sample business logic implementations.

With this template, you can quickly build a content-based web backend in just 1 minute and customize it for your own project.

🚀 Features
Frameworks & Core Technologies
Spring Boot 2.7.x
Spring MVC
MyBatis + MyBatis Plus (with pagination support)
Spring AOP (Aspect-Oriented Programming)
Spring Scheduler (Scheduled Tasks)
Spring Transaction Management
Data Storage
MySQL (Relational Database)
Redis (In-memory Database)
Elasticsearch (Search Engine)
Tencent Cloud COS (Object Storage)
Utilities & Libraries
EasyExcel (Excel Processing)
Hutool (Utility Toolkit)
Gson (JSON Parsing)
Apache Commons Lang3 (Utility Library)
Lombok (Java Annotations for Cleaner Code)
Business Features
Distributed Login with Redis Session
Global Request & Response Interceptor (for logging)
Centralized Exception Handling
Custom Error Codes & Unified API Response Format
Swagger + Knife4j (API Documentation)
Custom Authorization Annotations & Validation
Cross-Origin Resource Sharing (CORS) Handling
Fix for Long Integer Precision Loss
Multi-Environment Configuration
Prebuilt Business Functions
User Authentication (Register, Login, Logout, Profile Management, Role-Based Access Control)
Post Management (Create, Delete, Edit, Update, Database & Elasticsearch Search)
Like & Favorite System (Like, Unlike, Favorite, Retrieve Favorites)
Full & Incremental Sync with Elasticsearch
WeChat Open Platform & Public Account Support
File Uploading by Business Category
Testing
JUnit5 Unit Testing
Prebuilt Sample Test Cases
🏗 Project Setup
1️⃣ Database Setup (MySQL)
Update application.yml with your MySQL configuration:
yaml
Copy
Edit
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/my_db
    username: root
    password: 123456
Execute the SQL script located in sql/create_table.sql to create the required tables.
Start the project and access API Documentation at:
bash
Copy
Edit
http://localhost:8101/api/doc.html
2️⃣ Redis for Distributed Login
Configure application.yml for Redis:
yaml
Copy
Edit
spring:
  redis:
    database: 1
    host: localhost
    port: 6379
    timeout: 5000
    password: 123456
Set session storage to Redis in application.yml:
yaml
Copy
Edit
spring:
  session:
    store-type: redis
Remove RedisAutoConfiguration exclusion from MainApplication.java:
java
Copy
Edit
// Before:
@SpringBootApplication(exclude = {RedisAutoConfiguration.class})

// After:
@SpringBootApplication
3️⃣ Elasticsearch Search Engine Setup
Update application.yml for Elasticsearch:
yaml
Copy
Edit
spring:
  elasticsearch:
    uris: http://localhost:9200
    username: root
    password: 123456
Create an Elasticsearch index using the mapping in sql/post_es_mapping.json:
json
Copy
Edit
PUT post_v1
{
  // Parameters in sql/post_es_mapping.json
}
Enable Full & Incremental Sync from MySQL to Elasticsearch:
Open job/FullSyncPostToEs.java and job/IncSyncPostToEs.java.
Uncomment the @Component annotation to activate the synchronization tasks:
java
Copy
Edit
// @Component  // Uncomment to enable sync jobs
🚀 Quick Start
With this template, you can quickly launch a backend system with user authentication, post management, and search capabilities.

Clone the Repository
bash
Copy
Edit
git clone https://github.com/YourGitHubUsername/YourRepo.git
cd YourRepo
Start Backend
bash
Copy
Edit
./mvnw spring-boot:run
Access API Docs
Swagger UI: http://localhost:8101/api/doc.html
