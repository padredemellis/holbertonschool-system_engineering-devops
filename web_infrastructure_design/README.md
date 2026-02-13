# Web Infrastructure Design

## Description
This project is the first step in learning how to design and communicate complex network infrastructures. In this repository, I explore the components of a web stack, their roles, and how data flows from a user's request to a server's response.

Simple Web Stack
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

Distributed web infrastructure

1. Why add a Load Balancer?
Answer: To distribute incoming traffic across multiple servers. This prevents any single server from becoming overloaded and increases the availability of the website.

2. Distribution Algorithm (Round Robin)
How it works: The Load Balancer sends the first request to Server 1, the second to Server 2, the third back to Server 1, and so on. It’s like a dealer handing out cards in a circle.

3. Active-Active vs. Active-Passive
Active-Active: Both servers are working at the same time, sharing the load. (Este es el que estamos usando).

Active-Passive: Only one server is working. The second one is "sleeping" and only wakes up if the first one fails.

4. Database Primary-Replica (Master-Slave)
Primary (Master): Is the only one that can Write data (insert, update, delete).

Replica (Slave): Only Reads data. It synchronizes with the Primary to have the same information.

Difference: The application sends "save" actions to the Primary and "view" actions (like reading a profile) to the Replica to balance the work.

Secured and monitored web infrastructure

1. Why Firewalls?
Answer: To protect the servers from unauthorized access. They act as a filter that only allows legitimate traffic through specific ports (like 80 or 443).

2. Why HTTPS?
Answer: To encrypt the communication between the user and the server. This ensures that sensitive data (like passwords) cannot be stolen by "pirates" (hackers) during transit.

3. Why Monitoring?
Answer: To have visibility into the health of the infrastructure. It helps us detect if a server is down, if the CPU is too high, or if there is an error in the application.

How it collects data: The clients (agents) installed on each server send metrics (logs, usage) to a central service (like Sumologic) periodically.

Monitoring QPS (Queries Per Second): To monitor QPS, we need to analyze the Web Server logs (Nginx) and count how many requests are being processed every second.

## Author
* **Emanuel Romero** - Student at Holberton School.