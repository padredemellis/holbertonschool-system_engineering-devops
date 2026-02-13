# Web Infrastructure Design

## Description
This project is the first step in learning how to design and communicate complex network infrastructures. In this repository, I explore the components of a web stack, their roles, and how data flows from a user's request to a server's response.

## Task 0: Simple Web Stack
The goal of this task is to design a one-server infrastructure that hosts a website reachable via `www.foobar.com`.

### Diagram
![Web Application Request Flow](Web%20Application%20Request%20Flow.png)

### Infrastructure Details
* **Server:** A physical or virtual machine that provides resources and services to other computers (clients).
* **Domain Name:** A human-readable address (foobar.com) mapped to an IP address.
* **DNS Record Type:** The `www` in `www.foobar.com` is an **A record** because it points directly to the server's IP address (8.8.8.8).
* **Web Server (Nginx):** Manages HTTP requests and serves static content to the browser.
* **Application Server:** Processes the dynamic logic of the application and generates the content.
* **Database (MySQL):** A structured system to store, retrieve, and manage application data.
* **Communication:** The server and the user's browser communicate via the **HTTP protocol**.

### Identified Issues
1. **SPOF (Single Point of Failure):** If this single server fails, the entire website becomes unavailable.
2. **Downtime for Maintenance:** Updating code or software requires restarting services, which causes temporary service interruption.
3. **Scalability:** The infrastructure cannot handle high traffic loads as all resources are limited to one machine.

## Author
* **Emanuel Romero** - Student at Holberton School.