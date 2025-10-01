# CMSpit

This is a machine that allows us to practise web app hacking and privilege escalation using recent vulnerabilities.

## Task1

First we scan the machine using nmap
`nmap -sV --top-ports 1000 10.10.134.1`

![Alt Text](./assets/nmap.png)
Lets check port 80 on a web browser  
it brings us straight to a login page `http://10.10.134.1/auth/login?to=/`

![Alt Text](./assets/login_page.png)

### What is the name of the Content Management System (CMS) installed on the server?

<span style="color: green; font-weight: bold">Correct Answer: `Cockpit`</span>

### What is the version of the Content Management System (CMS) installed on the server?

<span style="color: green; font-weight: bold">Correct Answer: `0.11.1`</span>

### What is the path that allow user enumeration?

- Until now we don't have any credentials, i tried different random credentials, the server is always responding with the same response **Login failed**, this will not gonna help us to enumerate users since the response is the same for all inputs
- Lets check the forgot password page
  - When we enter a random username we get **User not found** message, except for the username `admin` i got **"Invalid address: (From): root@localhost"**, maybe this gonna help us later.
- Lets check the diffrent requests using **_Burpsuite_**
  ![Alt Text](./assets/login_req.png)
  this is strange, there is a csrf token in the req body

- Lets search on metasploit if there is any exploit
