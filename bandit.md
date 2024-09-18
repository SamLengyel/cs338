### Bandit Level 0 -> Level 1
- Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
- How to solve: you should end up in the home directory when you ssh in; do **ls** to find the spelling of readme, then **cat readme** to print the contents of readme: the password.
### Bandit Level 1 -> Level 2
- Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
- How to solve: run **cat ./-** to cat the contents of the file with the filename "-" in the home directory containing the password.
### Bandit Level 2 -> Level 3
- Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
- How to solve: run **cat spaces\ in\ this\ filename** to cat the contents of the file - using backslashes to escape the spaces. I used tab autocomplete rather than typing it all.
### Bandit Level 3 -> Level 4
- Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
- How to solve: run **cd inhere**, **ls -a** to show the hidden filename, and then **cat ...Hiding-From-You** to print the contents of the hidden file.
### Bandit Level 4 -> Level 5
- Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
- How to solve: run **cd inhere**, **ls**, and then sequentially **cat** the filenames with **cat ./filename** until you get one with human-readable text.
### Bandit Level 5 -> Level 6
- Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
- How to solve: run **cd inhere**, then **find . -size 1033c** to find the file with the correct size and **cat ./maybehere07/.file2** to print its contents.
### Bandit Level 6 -> Level 7
- Password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaji
- How to solve: run **find / -user bandit7 -group bandit6 -size 33c** to find the file with the correct attributes and choose the one result without **Permission denied** and run **cat /var/lib/dpkg/info/bandit7.password**
### Bandit Level 7 -> Level 8
- Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
- How to solve: run cat **data.txt | grep millionth** and then copy the password.
### Bandit Level 8 -> Level 9
- Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
- How to solve: run **sort data.txt | uniq -u** to sort the lines in data.txt and print the only unique line from the sorted output.
### Bandit Level 9 -> Level 10
- Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
- How to solve: run **vi data.txt**, search the file with /== and **n** to find the occurence near the password.
### Bandit Level 10 -> Level 11
- Password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
- How to solve: run **base64 -d data.txt** to decode the base64 encoding in data.txt.
### Bandit Level 11 -> Level 12
- Password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
- How to solve: run **cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'** to pass the content of data.txt to tr, rotate the upper and lowercase letters of the file 13 characters forwards (a to m, n to z, A to M, N to Z) to undo the ROT13 cipher and print the result to the terminal.
