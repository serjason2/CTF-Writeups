# Challenges
## The Fork Bomb
Step 1. write a small script (like in the Chaining Commands module)
- nano fork_bomb.sh

Step 2. make it executable (like in the Perceiving Permissions module)
- chmod ugo+x fork_bomb.sh

Step 3. make it launch a copy of itself in the background (like in the Processes and Jobs module)
- nano fork_bomb.sh
- Write script: ./fork_bomb.sh & ./fork_bomb.sh &
   - This script runs the bash shell in the background while executing a copy of the bash shell in the background, which totals up to two.
  
Step 4. and then launch another copy of itself in the background!
- Launch two terminals
- Terminal 1: run /challenge/check
- Terminal 2: run ./fork_bomb.sh
  
Wait to receive flag.

## Disk-Space Doomsday
Step 1. Fill your disk.
- yes > yes (redirecting yes into the yes file to fill up the disk)

Step 2. Run /challenge/check. It will attempt to create a 1 megabyte temporary file. If that fails, you pass the first stage and the checker will ask you to free the space.
- /challenge/check

Step 3. Delete the file you made (with rm) to clear up the space.
- rm yes

Step 4. Run /challenge/check a second time. If it can now create the temporary file (i.e., you successfully cleaned up your home directory), you’ll receive the flag.
- /challenge/check

## rm -rf /
- run /challenge/check (before rm -rf /)
- now run command: rm -rf /
   - -r: remove recursively, removes directories and all files contained in them.
   - -f: force remove (ignores any errors the rm command runs into or complications that it may have.)

## Life after rm -rf /
- rm -rf --no-preserve-root /
- now read the flag: read VAR < /flag
   - This redirects /flag as a standard input into VAR
- echo $VAR 

## Finding meaning after rm -rf /
- rm -rf --no-preserve-root /
- echo /* (to print out all directories available) (find the random generated named file)
   - echo is a built-in command
   - want to do /* b/c the random generated file is in the root directory rather than the home directory.
- read flag < {find the random file}
- echo $flag
