# TryHackMe: 2025 Advent of Cyber (Day 1)
**Room Name**: Linux CLI - Shell Bells (my own notes)

### Introduction
- **tbfc-web01** - a Linux server processing Christmas wishlists
- Every data tells a story, and this data lies the truth that traces McSkidy's final actions, or perhaps the clues to King Malhare's twisted vision for **EASTMAS**
<br>

**The Learning Objectives for this room are:**
- Learning the basics of the Linux command-line interface (CLI)
- Explore its use for personal objectives and IT administration
- Applying your knowledge to unveil the Christmas mysteries

Now, connect to the virtual machine (VM) or you can connect via your own THM VPN connected machine with the credentials that are provided.

### Linux CLI (Command-Line Interface)
List of Basic Linux Commands or Files
```
- echo "Hello World!"
- ls
  - -la
- cat README.txt
- pwd
- grep
- find
- /var/log
- auth.log
- .sh are shell scripts and are used by both IT teams to automate things and by attackers to quickly run malicious commands.
```

- Which CLI command would you use to list a directory? ls
  - Identify the flag inside of the McSkidy's guide: make sure you’re not root and you’re in as mcskidy user, if you’re in root, type exit to return to the user mcskidy. Type pwd, and if you’re not in the home directory ~, type cd ~, now change into the /home/mcskidy/Guides directory and type ls -la to view the hidden files and file permissions and cat the hidden guide

- What flag did you see inside of the McSkidy's guide? THM{learning-linux-cli}

- Which command helped you filter the logs for failed logins? grep

- What flag did you see inside the Eggstrike script? THM{sir-carrotbane-attacks}
  - change directory to SOCMAS/2025, and cat the eggstrike shell script

- Which command would you run to switch to the root user? sudo su

- Finally, what flag did Sir Carrotbane leave in the root bash history? THM{until-we-meet-again}
<br>


For those who consider themselves intermediate and want another challenge, check McSkidy's hidden note in `/home/mcskidy/Documents/` to access the key for **Side Quest 1**.
- Switch user to “eddi_knapp” and enter password if prompted.
    - sudo su eddi_knapp
    - Change directory to /home/eddi_knapp/Documents/
    - This is where message file is encrypted via GnuPG, and our goal is to find the passcode to decrypt the .gpg file.
    - There are 3 passwords that need to be found in order to decrypt the .gpg file
    - PASSFRAG1: used the `find -name *pass*` to find that it was given output `./fix_passfrag_backups_20251111162432` I changed directory into that directory and listed the hidden files and file permissions, and `cat .profile.bak` or `cat .pam_environment.bak`
        - PASSFRAG1: “3ast3r”
    - PASSFRAG2: n/a
        - n/a
    - PASSFRAG3: Inside Pictures directory and is hidden, use `ls -la` to find the hidden easter egg.
        - PASSFRAG3: c0M1nG
