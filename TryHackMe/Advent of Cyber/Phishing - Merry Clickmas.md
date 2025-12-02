# TryHackMe: 2025 Advent of Cyber (Day 2)
**Room Name**: Phishing - Merry Clickmas (my own notes w/ some provided notes via THM room)

### Introduction
There have been several cybersecurity incidents lately against The Best Festival Company (TBFC), and the red teamers are providing security awareness training for employees in the hopes of increasing their knowledge in the future, and for the holiday season coming up with the rise of cyber attacks. The red teamers hope that employees are carefully looking and double-checking each link before clicking, and to not fall for phishing emails.<br>

**The learning objectives for this room:**
- Understand what social engineering is
- Learn the types of phishing
- Explore how red teams create fake login pages
- Use the Social-Engineer Toolkit to send a phishing email<br>

**Social Engineering** is the process of manipulating individuals with different techniques to lure them into providing their sensitive information

**Phishing** is when emails are sent to specific target(s)/individuals acting as a trusted entity in the hopes of them providing their sensitive information.
  - **Types of phishing**:
    - Smishing (short-text messages)
    - Vishing (voice calls)
    - Quishing (malicious QR codes)
<br>
   
### Phishing Exercise for TBFC
We'll be using the Social-Engineer Toolkit to send the phishing email to lure the target to clicking on the fake web login page link
- Download the provided tasks if not in the AttackBox
- Change into the ~/Rooms/AoC2025/Day02 directory and type `./server.py` to start the C2 server to listen for traffic from your fake login page
- Now open a different terminal and type `setoolkit` to start the Social-Engineer toolkit (you should see a `set>` on your terminal screen that means you're in a correct spot. (follow steps below)
  - Press 1) Spear-Phishing Attack Vectors
  - Press 5) Mass Mailer Attack
  - Press 1. E-Mail Attack Single Email Address
1. Send email to: Let’s begin by targeting factory@wareville.thm
2. How to deliver the email: We will choose Use your own server or open relay
3. From address: We know that the guys at the toy factory communicate regularly with Flying Deer, the shipping company, so that we will use updates@flyingdeer.thm as the source email address
4. From name: Let’s use the name Flying Deer
5. Username for open-relay: We will leave it blank and just hit the Enter key
6. Password for open-relay: We will leave it blank and just hit the Enter key
7. SMTP email server address: We will deliver directly to the TBFC mail server by entering `10.65.181.191` (should be your attacker IP address on THM).
8. Port number for the SMTP server: We leave the default value of 25 and just hit the Enter key

9. Flag this message as high priority: The choice is entirely up to you, depending on your knowledge of the circumstances, but we will answer with no
10. Do you want to attach a file: We will answer with n
11. Do you want to attach an inline file: Again, let’s answer with n

12. Email subject: We need to think of something convincing, for example, “Shipping Schedule Changes”
13. Send the message as HTML or plain: We will keep the default choice of plaintext and just hit the Enter key
14. Enter the body of the message, and type END (capitals) when finished: Create and type any convincing message. Make sure to include the URL `http://10.65.114.184:8000` (this is your machine IP address) to check if the target will fall for this trick.

Now wait and monitor your C2 server to see if the target enters their credentials. If they do, note down their credentials you will need it for the questions.
