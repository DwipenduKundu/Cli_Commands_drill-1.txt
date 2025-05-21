# Practice Drill 1

##  Questions
* Create the following directory structure. (Create empty files where necessary)

```
hello
├── five
│   └── six
│       ├── c.txt
│       └── seven
│           └── error.log
└── one
    ├── a.txt
    ├── b.txt
    └── two
        ├── d.txt
        └── three
            ├── e.txt
            └── four
                └── access.log
```

* Delete all the files having the .log extension
* Add the following content to a.txt
```  
  Unix is a family of multitasking, multiuser computer operating systems that derive from the original AT&T Unix, development starting in the 1970s at the Bell Labs research center by Ken Thompson, Dennis Ritchie, and others 
```
* Delete the directory named five
* Rename the one directory to uno
* Move a.txt to the two directory

## Answers
#### 1st answer
```
#Creating all directories
mkdir hello                        #create 'hello' directory
mkdir hello/five                   #create 'five directory 
mkdir hello/five/six               #create 'six' directory
mkdir hello/five/six/seven         #create 'seven' directory
mkdir hello/one                    #create 'one' directory
mkdir hello/one/two                #create 'two' directory
mkdir hello/one/two/three          #create 'three' directory
mkdir hello/one/two/three/four     #create 'four' directory

#Creating all txt and log files
touch hello/five/six/c.txt              #creating "c" text file  
touch hello/five/six/seven/error.log    #creating "error" log file
touch hello/one/a.txt                   #creating "a" text file
touch hello/one/b.txt                   #creating "b" text file
touch hello/one/two/d.txt               #creating "d" text file
touch hello/one/two/three/e.txt         #creating "e" text file
touch hello/one/two/three/four/access.log   # creating "access" log file
```
#### 2nd answer

```
rm *.log            #to delete all .log files only from the current directory
find hello -type f -name "*.log" -delete    #to delete all .log files
```

#### 3rd answer
```
#for adding the text into the existing file
echo "Unix is a family of multitasking, multiuser computer operating systems that derive from the original AT&T Unix, development starting in the 1970s at the Bell Labs research center by Ken Thompson, Dennis Ritchie, and others" > hello/one/a.txt

#can see the content
cat hello/one/a.txt
```

#### 4th answer
```
#to delete the non empty directory
rm -r hello/five
```

#### 5th answer
```
#rename the 'one' directory into 'uno' directory
mv hello/one hello/uno
```

#### 6th answer
```
#change the directory location of a.txt i.e move to another location
mv hello/uno/a.txt hello/uno/two/
```

# Practice Drill 2

##  Questions
### Pipes
  ##### 1 Download the contents of "Harry Potter and the Goblet of fire" using the command line from [here](https://raw.githubusercontent.com/bobdeng/owlreader/master/ERead/assets/books/Harry%20Potter%20and%20the%20Goblet%20of%20Fire.txt)
  ##### 2 Print the first three lines in the book
  ##### 3 Print the last 10 lines in the book
  ##### 4 How many times do the following words occur in the book?
        * Harry
        * Ron
        * Hermione
        * Dumbledore
  ##### 5 Print lines from 100 through 200 in the book
  ##### 6 How many unique words are present in the book?


### 1st answer
```
#Installing curl and by using of curl we can import the harry.txt file from the given link
sudo apt-get install curl
curl -o harry.txt https://raw.githubusercontent.com/bobdeng/owlreader/master/ERead/assets/books/Harry%20Potter%20and%20the%20Goblet%20of%20Fire.txt
```

### 2nd answer
```
#1st 3 lines output
head -n 3 harry.txt
```

### 3rd answer
```
#last 10 lines output
tail -n 10 harry.txt
```

### 4th answer
```
#command for finding those words:

grep -iow 'Harry' harry.txt | wc -l

grep -iow 'Ron' harry.txt | wc -l

grep -iow 'Hermione' harry.txt | wc -l

grep -iow 'Dumbledore' harry.txt | wc -l
```

### 5th answer
```
# Display lines 100 to 200
sed -n '100,200p' harry.txt                    
```

### 6th answer
```
# Count unique words
tr -d '[:punct:]' < book.txt | tr '[:upper:]' '[:lower:]'| tr -s '[:space:]' '\n' | sed 's/^[[:space:]]//' | sed 's/^[[:space:]]//' | sort | uniq | wc -l 
```

##  Questions
### Processes, ports
#### 1 List your browser's process ids (pid) and parent process ids(ppid)
#### 2 Stop the browser application from the command line
#### 3 List the top 3 processes by CPU usage.
#### 4 List the top 3 processes by memory usage.
#### 5 Start a Python HTTP server on port 8000
#### 6 Open another tab. Stop the process you started in the previous step
#### 7 Start a Python HTTP server on port 90
#### 8 Display all active connections and the corresponding TCP / UDP ports.
#### 9 Find the pid of the process that is listening on port 5432

#### Answers
```
ps -eo pid,ppid,comm | grep -i 'chrome'             # List browser PIDs and PPIDs
pkill -f chrome                                     # Terminate all Chrome processes
ps -eo pid,ppid,cmd,%cpu --sort=-%cpu | head -n 4   # Top 3 processes by CPU usage
ps -eo pid,ppid,cmd,%mem --sort=-%mem | head -n 4   # Top 3 processes by memory usage
python3 -m http.server 8000                         # Start HTTP server on port 8000
lsof -i :8000                                       # List processes using port 8000
kill <PID>                                          # Terminate process with specified PID
sudo python3 -m http.server 90                      # Start HTTP server on port 90 with sudo
netstat -tuln                                       # Display all active connections and listening ports
sudo lsof -i :5432                                  # Find PID of process using port 5432
```

##  Questions
### Managing software
* Use apt (Ubuntu) or homebrew (Mac) to:
    * Install htop, vim and nginx
    * Uninstall nginx

### Answers:
```
sudo apt update                     # Update package list (Ubuntu)
sudo apt install htop vim nginx     # Install htop, vim, nginx
sudo apt remove nginx               # Uninstall nginx
```
##  Questions
### Misc
* What's your local IP address?
* Find the IP address of google.com
* How to check if Internet is working using CLI?
* Where is the node command located? What about code?

### Answer
```
hostname -I                         # Display local IP address
nslookup google.com                 # Find IP address of google.com
ping -c 4 google.com                # Check internet connectivity
which node                          # Locate node command
which code                          # Locate code (VS Code) command
```

---------------------------------------------------

# Linux Command Quick Revision Notes

## Directory Management

| **Command**      | **Description**                        |
|------------------|----------------------------------------|
| `mkdir <name>`   | Create a new directory                 |
| `cd <name>`      | Navigate into the specified directory  |
| `cd ..`          | Navigate back to the parent directory  |
| `rm -R <name>`   | Recursively delete a directory         |
| `mv <old> <new>` | Rename or move a directory             |

---

## File Operations

| **Command**            | **Description**                          |
|------------------------|------------------------------------------|
| `touch <file>`         | Create a new file                        |
| `nano <file>`          | Open a file in `nano` editor             |
| `cat <file>`           | Display the contents of a file           |
| `mv <file> <dir>/`     | Move a file to a directory               |

---

## Find and Delete Logs

| **Command**                                  | **Description**                                           |
|---------------------------------------------|-----------------------------------------------------------|
| `find . -name "*.log" -type f`              | List all `.log` files in current directory and subdirs    |
| `find . -name "*.log" -type f -delete`      | Delete all `.log` files from current directory recursively|

---

## Permissions

| **Command**                            | **Description**                                    |
|----------------------------------------|----------------------------------------------------|
| `chmod 755 <file>`                     | Set file permissions to `rwxr-xr-x`                |
| `chmod -R 755 <directory>`             | Recursively set permissions for a directory        |

---

## System Information & Utilities

| **Command**         | **Description**                             |
|---------------------|---------------------------------------------|
| `ps -A` or `ps -e`  | Show all running processes                  |
| `firefox &`         | Launch Firefox in the background            |
| `whoami`            | Display current logged-in username          |
| `groups`            | Show groups the user belongs to             |
| `uname -m`          | Show machine hardware name (architecture)   |

---

## Download and Explore Book

| **Command**                                          | **Description**                                                   |
|------------------------------------------------------|-------------------------------------------------------------------|
| `curl -O https://www.gutenberg.org/cache/epub/223/pg223.txt` | Download the book                                                 |
| `head -n 3 pg223.txt`                                | Print the first 3 lines of the book                               |
| `tail -n 10 pg223.txt`                               | Print the last 10 lines of the book                               |
| `grep -o -i 'Harry' pg223.txt \| wc -l`              | Count occurrences of "Harry"                                      |
| `grep -o -i 'Ron' pg223.txt \| wc -l`                | Count occurrences of "Ron"                                        |
| `grep -o -i 'Hermione' pg223.txt \| wc -l`           | Count occurrences of "Hermione"                                   |
| `grep -o -i 'Dumbledore' pg223.txt \| wc -l`         | Count occurrences of "Dumbledore"                                 |
| `sed -n '100,200p' pg223.txt`                        | Print lines 100 through 200 in the book                           |
| `tr -d '[:punct:]' < harry.txt \| tr '[:upper:]' '[:lower:]'\| tr -s '[:space:]' '\n' \| sed 's/^[[:space:]]//' \| sed 's/^[[:space:]]//' \| sort \| uniq \| wc -l` | Count unique words in the book  |

---

## Processes and Ports

| **Command**                                      | **Description**                                                   |
|--------------------------------------------------|-------------------------------------------------------------------|
| `ps aux \| grep firefox`                         | List browser's process IDs and parent process IDs                 |
| `pkill firefox`                                  | Stop Firefox browser from command line                            |
| `ps -eo pid,ppid,%cpu,cmd --sort=-%cpu \| head -n 4` | List top 3 processes by CPU usage                              |
| `ps -eo pid,ppid,%mem,cmd --sort=-%mem \| head -n 4` | List top 3 processes by memory usage                           |

---

## Python Server and Network

| **Command**                      | **Description**                                           |
|----------------------------------|-----------------------------------------------------------|
| `python3 -m http.server 8000`    | Start a Python HTTP server on port 8000                  |
| `lsof -i :8000`                  | Find PID of process on port 8000                         |
| `kill <PID>`                     | Stop Python HTTP server                                  |
| `python3 -m http.server 90`      | Start a Python HTTP server on port 90                    |
| `netstat -tuln`                  | Display all active connections and TCP/UDP ports         |
| `sudo lsof -i :5432`             | Find PID of process listening on port 5432               |

---

## Managing Software (Debian-based with apt)

| **Command**                           | **Description**                     |
|----------------------------------------|-------------------------------------|
| `sudo apt update`                      | Update package list                 |
| `sudo apt install htop vim nginx -y`  | Install htop, vim, and nginx        |
| `sudo apt remove nginx -y`            | Uninstall nginx                     |

---

## Miscellaneous

| **Command**               | **Description**                            |
|---------------------------|--------------------------------------------|
| `hostname -I`             | Show your local IP address                 |
| `ping -c 1 google.com`    | Get IP address of google.com and test DNS  |
| `ping -c 1 8.8.8.8`       | Check if Internet works using Google DNS   |
| `which node`              | Find the location of the node command      |
| `which code`              | Find the location of the code command      |

---
