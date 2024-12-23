## Blind SQL Injection - Dockerized

This project provides a Dockerized environment to simulate and test **Blind SQL Injection** attacks in a secure and isolated setup. 
The goal is to help users understand the mechanics of this attack, how it differs from traditional SQL Injection, and how to experiment with it using practical examples.

---

## What is Blind SQL Injection?

### Difference Between SQL Injection and Blind SQL Injection

**SQL Injection** allows attackers to directly view the results of their malicious queries, such as database errors or data displayed on the webpage. It is fast and straightforward since the output is immediately visible.

**Blind SQL Injection**, however, does not show direct results. Instead, attackers infer information by observing the application’s behavior (e.g., response times or changes in output). It is slower and more complex but can still extract sensitive data with persistence. 

---

## Prerequisites
To run the Dockerized application, ensure the following are installed on your system:

Docker (required to load and run the image)
Git (optional, for cloning the repository)
System with at least 2GB of free space (the image size is ~801 MB)

---

## Installation and Usage : 

Follow these steps to set up and run the application:

1. Clone the Repository
If you haven't already, clone the repository from GitHub:
```sql
git clone https://github.com/ALAOUIa/Blind_SQL_Injection-App.git
cd Abdelaziz_Blind-SQL-Injection-Dockerized

2. Load the Docker Image
Load the prebuilt Docker image from the .tar file:
```sql
docker load -i Abdelaziz_Blind-SQL-Injection-Dockerized.tar

3. Run the Docker Container
Start the container with the following command:
```sql
docker run -p 8080:80 Abdelaziz_Hacker


4. Access the Application
Open your browser and navigate to:
```sql
http://localhost:8080

5. Test SQL Injection Attacks
Use the examples provided in the Examples section to test Blind SQL Injection on the vulnerable endpoints.


## Examples of Blind SQL Injection Attacks

Here are some sample payloads to test on the vulnerable application:

### 1. **Boolean-Based Blind SQL Injection**
This method evaluates responses based on a condition:
```sql
' OR 1=1 --   # True condition, bypasses authentication
' OR 1=2 --   # False condition, does not bypass
