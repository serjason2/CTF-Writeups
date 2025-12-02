**Tags**: #healthcare, #ransomware, #double-extorsion

# **My notes on Jojo's Hospital case**
### Crypto - but the bad king
- The name of the ransomware group is “Lock Byte” and they encrypted their files and JoJo’s Hospital only has 72 hrs left to pay the fee to decrypt their files if not, their sensitive information will be released to the dark web/public/online
- 6,420 files are encrypted at the hospital
- lockbyte_ransomer.exe → spread_ransomware.exe
- patient_data_exporter.exe → used to steal patients data
- A `curl`command is like a digital delivery service
    - Imagine you're sending a package to a friend far away. You pack up the item, write the address on the box, and then hand it to the delivery person who takes it to your friend's house.
    - Similarly, a curl command packs up the stolen data, addresses it to an external server, and sends it over the internet.
        - This way, the attackers can quickly and quietly move the stolen data from the hospital’s computers to their own remote server.
    - secure-health-access[.]com (this is where the TA send the stolen data to, which is their own external server)

- **What command did they use to clear their tracks? Copy and paste the full command.**
    - cmd.exe /c del C:\Users\andavis\Documents\patient_data_*.zip

- The threat actor logged into Anthony Davis machine/account and downloaded a ransomware spreader internally so it encrypted every patients account. The TA logged in from 203.0.113.1 src ip<br>

### Sharks in the hospital water
- Anthony Davis credentials were hacked
- The credentials were apparently purchased via the dark web from another hacking group
- How did the hackers get access to Davis’ credentials?
    - Typosquatting from wanting to purchase raising canes, as there were a raising canes across the street from Jojo’s hospital
    - 26 total web requests clicked on the fake raising canes domain
    - 24 unique internal employees IP addresses clicked on the fake domain
    - The fake raising canes website redirected the user to a malicious domain, and .pdf / .docx file
    - The attackers did a lot of recon and focused on Anthony Davis account and stole network diagrams, credentials, and compressed it into a zip file to attract less attention and sent the data via the `cURL` command to the external domain of nothing-to-see-here[.]net<br>
 
### Recap and Lessons Learned
In this module, we investigated a cyber attack at JoJo's Hospital in Lexington, Kentucky. The attack involved two groups of hackers: SharkFin7 and the LockByte ransomware group. Here's what happened and what we learned:

**Recap of the Incident:** JoJo's Hospital was targeted by hackers who used a fake advertisement to trick hospital employees into downloading harmful files. This allowed the first hacker group, SharkFin7, to access the hospital's network and steal information. SharkFin7 then sold this access to the LockByte ransomware group. LockByte used this access to lock important files and demanded money from the hospital and its patients to unlock them.

**What We Learned:**

1. **How Hackers Get In:**
    - **Phishing and Fake Ads:** Hackers can trick people into clicking fake ads and downloading harmful files. It's important to be careful about what you click and download.
2. **What Hackers Do Once Inside:**
    - **Manual Hacking:** After getting in, hackers can move around the network, steal information, and set up for more attacks.
3. **Hackers Working Together:**
    - **Selling Access:** Some hackers break in and then sell that access to other hackers who can do more damage, like LockByte.
4. **Ransomware Attacks:**
    - **Locking Files:** Ransomware groups lock important files and demand money to unlock them. This can be very harmful, especially for places like hospitals.
5. **Investigating Attacks:**
    - **Finding Clues:** By looking at different data sources, we can trace the hackers' actions and understand how the attack happened.

By investigating this attack, we learned important skills to detect, analyze, and respond to cyber threats. We saw how careful monitoring and quick action can help protect important data and keep services running smoothly.
