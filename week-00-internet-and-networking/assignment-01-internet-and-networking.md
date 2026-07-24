# Week 00 - Internet and Networking

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

# 🧑‍💻 Task 1: Using ChatGPT as Your Learning Assistant

## Scenario

You're new to DevOps and will frequently encounter technical questions. ChatGPT can be your learning companion.

## Your Task

Write a clear ChatGPT prompt to help you understand:

> "What is a protocol in networking? Explain with a simple real-life example."

Take a screenshot of your interaction showing:

* Your detailed prompt (with clear expectations)
* ChatGPT's simplified response with an example

## Screenshot

Save your screenshot in the `screenshots` folder and update the file name below.

![Task 1 Screenshot](screenshots/task-1-chatgpt.png)


Replace `task-1-chatgpt.png` with your actual screenshot file name.

---

## What I Learned (2–3 lines)

-dATA
-PACKAGING
-RULE
-TRANSMISSION

---

# 🌐 Task 2: Internet and Networking

## Scenario

Your friend is launching an online bookstore named **EpicReads**.

He asked you to explain how users globally can access his website hosted in Finland.

## Your Task

Write a short explanation (**100–150 words**) that includes:

* Packet Switching
* IP Address
* TCP/IP
* HTTP/HTTPS

💡 **Tip:** You may use ChatGPT (as demonstrated in Task 1) to refine your explanation.

## Answer

Online book store EpicReads has a unique website and is hosted in Finland.This website address starts with http(80 port number and is unsecure communication) or https(secure communication uses 443 port number). HTTPS also encrypts the data, 
keeping user information safe . User URL request travels across the internet using packet switching, where data is broken into small packets and sent separately, then reassembled at the destination.When a user uses DNS name of this bookstore address to reach the website from anywhere in the world, behind the scene it uses packet switching, where data is broken into small packets and sent separately, then reassembled at the destination. Domain name system resolves to IP address by 
checking cache, asking DNS resolver, checking in root server, checking the top level domain server , and then finding IP and connecting to the website. Overall this communication needs reliability, what ever send ,should receive it in the destination and in the same order.This process uses TCP/IP protocol suite , which ensures all packets 
arrive correctly and in order, while IP handles routing them across networks. Together, these technologies allow anyone globally to access EpicReads quickly and reliably. 

---

# 🏗️ Task 3: Application Architecture & Stack

## Scenario

EpicReads bookstore has two application versions:

### Two-Tier Application

* Frontend
* Database

### Three-Tier Application

* Frontend
* Backend
* Database

## Your Task

* Draw simple diagrams (hand-drawn or tool-based such as draw.io)
* Label each layer clearly
* List at least two common technologies or tools used for each layer
* Submit a screenshot or photo clearly showing your own drawing

## Diagram Screenshot / Photo

Save your diagram image in the `screenshots` folder and update the file name below.

![Application Architecture Diagram](screenshots/task-3-diagram.png)


Replace `task-3-diagram.png` with your actual diagram file name.

---

## Technologies Used

### Frontend

* HTML, CSS and Java Script 

### Backend

*Node.js , python(Flask, Django) 

### Database

*  My SQL and Postgre SQL 

---

# 🌍 Task 4: Domain Name & DNS (Basic Concepts)

## Scenario

Your friend's bookstore **EpicReads** is currently accessible through:

```text
52.172.142.222:3000
```

He purchased the domain:

```text
epicreads.com
```

## Your Task

In **50–100 words**, explain in your own words:

1. What is DNS (Domain Name System)?
2. Which DNS record type should be used to connect the domain to the given IP, and why?

## Answer

Bookstore EpicReads, purchased a domain: epicreads.com where .com is the root 
server of this domain. When a URL enter the domain name, it resolves to Ip: port for 
52.172.142.222:3000. 3000 is the port number and 52.172.142.222 is the internet 
protocol number. It is hard to remember this IP number for a human, hence introduced 
more friendly naming as DNS (domain name system). We can consider it as a internet’s 
phonebook- which translates human friendly domain name (here epicreads.com) to 
machine readable IP address (here 52.172.142.222). Hence the user can see the 
website content. Not always website can be viewed in 80 or 443 port, but some custom 
port, like 3000.
When purchase DNS from route 53 or other providers, there is a record type(A ,AAAA, 
CNAME type,MX recorder, TXT recorder). Basically, A record type maps a domain name 
directly to an Ipv4 address, so that DNS can resolve to correct IPv4 address. In case the 
website use IPv6, then AAAA record the matched one.

---

# 💻 Task 5: Visual Studio Code Setup (Hands-on)

## Your Task

Install Visual Studio Code (if not already installed).

Take a screenshot of your VS Code environment showing:

* Terminal open inside VS Code
* Running a basic command:

### Windows

```powershell
dir
```

### Linux / macOS

```bash
pwd
ls
```

* Your selected VS Code theme clearly visible

⚠️ **Important:** The screenshot must show your username or another identifiable detail to confirm it is your environment.

## Screenshot

Save your screenshot in the `screenshots` folder and update the file name below.

![VS Code Setup Screenshot](screenshots/task-5-vscode.png)


Replace `task-5-vscode.png` with your actual screenshot file name.

---

# 🔗 Task 6: Publish Your Assignment as a LinkedIn Post

## Objective

Publishing on LinkedIn helps you:

* Build your professional online presence
* Reinforce your learning
* Document your DevOps journey publicly

## Your Task

Summarize your answers from Tasks 1–5 into a LinkedIn post.

Clearly structure your post into the following sections:

* ChatGPT
* Internet & Networking
* App Architecture
* DNS
* VS Code Setup

Add the following credit note at the end of your post:

> **P.S. This post is part of the DevOps Micro Internship (DMI) with Agentic AI — Cohort 3 — by Pravin Mishra. My graded progress is public: https://dmi.pravinmishra.com/s/YOUR-GITHUB-USERNAME.html · Start your DevOps journey: https://dmi.pravinmishra.com/?utm_source=student&utm_medium=ps-linkedin&utm_campaign=cohort3**

---

## LinkedIn Post URL

Paste your LinkedIn post URL here:

```https://www.linkedin.com/posts/blessy-s-06b379269_to-ensure-that-i-am-industry-ready-to-take-activity-7440680650346704896-h5-S?utm_source=share&utm_medium=member_desktop&rcm=ACoAAEG6aBMB0zfBR9hQTWrl7i6zZCygzNyvY74
```

---

## LinkedIn Post Backup Copy

Paste the full text of your LinkedIn post here:
```
To ensure that I am industry ready to take any coming IT changes (with emerging AI era) I start my learning in a clear and structured way with cohort as keep in my mind that consistency is the key to success 👍 . Basic understanding of below points is key to start of any learning at any point of time in career switches
ChatGPT: Learn and practise precise and clear prompt to get best answers from your agent
Internet & Networking: Without knowing what and how internet and networking flows, it will be hard to understand applications itself. Packet switching, TCP, HTTPS are basic terminologies on it.
App Architecture: Architecture is like a blueprint. When I work with project, immediate attention pays in architectural diagram, which gives you a thorough knowledge on the structure of application whether 2 tier ,3 tier or microservice based and its technologies in each stack.
DNS: Domain name system is like internet’s phone book for conversion of human friendly domain names to machine readable ip address.
VS Code Setup: When ever I need to work on development, my priority is to work with Visual studio Code
P.S. This post is part of the FREE DevOps Micro Internship Cohort run by Pravin Mishra. You can start your DevOps journey for free from his YouTube Playlist.

**P.S. This post is part of the DevOps Micro Internship (DMI) with Agentic AI — Cohort 3 — by Pravin Mishra. 
My graded progress is public: https://lnkd.in/d5jnG2fH · 
Start your DevOps journey:
https://lnkd.in/dB8C7bcd```
---

# Reflection – Week 0

### What did you find easy?

I feel the flow and structure of course is easy

---

### What was difficult?

Writing articles feels me difficult.

---

### What will you improve next week?

Publish more facts into medium and social media by next week.

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.


## 📌 Resources

- 🌐 **DMI Official Website:** https://pravinmishra.com/dmi  
- 🎓 **DevOps for Beginners (Udemy):** https://www.udemy.com/course/devops-for-beginners-docker-k8s-cloud-cicd-4-projects/  
- 🎓 **Ultimate Agentic AI DevOps with Clude Code** https://www.udemy.com/course/ultimate-agentic-ai-devops-with-claude-code/?referralCode=448389767BC96284087B
- 🎓 **DevOps with Claude Code: Terraform, EKS, ArgoCD & Helm** https://www.udemy.com/course/devops-with-claude-code-terraform-eks-argocd-helm/?referralCode=1C5B734505D65A010FA3
- ▶️ **YouTube Playlist (DMI Cohort 3):** https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 **Pravin Mishra (LinkedIn):** https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 **CloudAdvisory (LinkedIn):** https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track*