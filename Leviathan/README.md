# Level 0
- Use the command `ls -la` to locate the hidden folder `~/.backups` containing `bookmarks.html`.
- Search for either `leviathan1` or `password` and find the password in plaintext.

# Level 1
- Find the binary `check` in the home directory which requires password.
- Disassemble binary using radare2 to find strings.
- Find the strings being used in strcmp() function to find correct password for binary.
- Reach a shell with `leviathan2` permissions and locate password in `/etc/leviathan_pass`.

# Level 2
- Find the binary `printfile` in the home directory with owner set as `leviathan3`.
- Disassemble it to find two functions, access() and /bin/cat being used.
- Since the access() function checks permission and the cat command simply prints it without any check, we can exploit it.
- Create a new directory in /tmp and create a file test.txt with random text to test printfile's functionality.
- Next, use exploit the access() function by running the command `touch pass\ test.txt`, creating a file named "pass test.txt".
- Run `~/printfile "pass test.txt"` and you will find that even though the file pass doesn't exist, it will print out contents of test.txt, thus exploiting access().
- Use this exploit along with soft linking the password file and get the password.

# Level 3
- You will find a binary `level3` in the home directory.
- Use ltrace on it and you will find strcmp doing plaintext comparison for entered password.
- Use that to get shell as `leviathan4` and locate password in `/etc/leviathan_pass`.

# Level 4
- Run the command `ls -la` to find a hidden directory ~/.trash.
- Find a binary which prints characters in binary.
- Convert to ASCII to get password.

# Level 5
- Find a binary `leviathan5` in home directory and run it empty with ltrace to check what it does.
- Create a file /tmp/file.log and fill it with random text to check the functionality of binary.
- Link the file.log with the password file from `/etc/leviathan_pass` to print out password.

# Level 6
- Find a binary leviathan6 which requires a 4 digit PIN to open shell as leviathan7.
- Brute force the PIN using a for loop and some bash scripting and wait for the shell to pop up.
- Get password from /etc/leviathan_pass.