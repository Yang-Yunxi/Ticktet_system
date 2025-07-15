## Online Ticketing System for High Concurrency Scenario

### 1. Development Environment Requirements

#### 1). Hardware Requirements
At least 8GB of RAM and 20GB of available disk space.<br>
Windows 10/11, macOS 10.15+, or Linux (recommended Ubuntu 20.04+).

#### 2). Software Requirements
JDK 17 <br>
Maven 3.6+ <br>
Node.js 14+ <br>
MySQL 5.7+ <br>
Redis 5+ <br>
Nacos 2.1.2 <br>
RocketMQ 4.5.1 <br>

### 2. Environment Deployment Process

#### 1). Back-end Service Deployment
Java Environment Configuration:<br>
Install JDK 17 and configure the JAVA_HOME environment variable.<br>
Verification: java -version should display version 17.x.

Database Preparation:<br>
Install MySQL 5.7+.<br>
Execute the initialization SQL script.

Middleware Configuration:<br>
a) Nacos 2.1.2:<br>
Start in standalone mode.<br>
Import the configuration set provided by the project (namespace/configs).<br>

b) Redis:<br>
Set up password protection.<br>
Configure maximum memory limit.<br>

c) RocketMQ 4.5.1:<br>
Start the NameServer.<br>
Start the Broker.<br>
Create the necessary topics for the project.<br>

#### 2). Project Build and Startup:
mvn clean install -DskipTests.<br>
Modify the middleware connection configuration in the application.yml of each module.<br>
Start services in the following order: <br>
Aggregated Service  → Gateway Service.<br>

#### 3). Front-end Service Deployment
Install Node.js 14+ and yarn/npm.<br>
Verification: node -v and npm -v.<br>

#### 4). Project Configuration:<br>
Modify the API base address in .env.development.<br>
Configure proxy to resolve cross-origin issues.<br>
Install dependencies: yarn install or npm install.<br>
Start: yarn serve or npm run serve.<br>
Access: http://localhost:8081.