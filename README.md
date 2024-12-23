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
cd Abdelaziz_Blind-SQL-Injection-Dockerized
