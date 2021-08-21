# AWK and SED
**Awk** is a powerful command which is used for pattern matching, manipulating and generating reports as well as text processing.

**Sed** is also powerful *Unix/Linux* command for editing a stream of text. Sed command is used to search, find, replace, insertion or delete.

-------
## AWK

Awk is a *domain-specific language* designed for text processing and typically used as data extraction and reporting tool like sed and grep. It is initially developed in 1977 by **Alfred Aho, Peter Weinberger,** and **Brian Kernighan**.

### __Structure of AWK__

![Workflow](https://www.linuxcommands.site/wp-content/uploads/2019/04/awk-workflow-1024x978.jpg)

#### **BODY Block**
This block is the core block of the awk command. It has three parts read, execute and repeat.

#### **1. Read**

AWK reads a line from the input stream (file, pipe, or stdin) and stores it in memory.

#### **2. Execute**

All awk commands are applied sequentially on the input. AWK executes commands for each line entered. However, we can restrict it to a specified pattern.

#### **3. Repeat**

This process repeats until the file reaches its end.

### **Installation from Source Code**

1. Step-1

```bash
vasanth@vasanth:~$ sudo apt-get update -y
 ```

2. Step-2

```bash
vasanth@vasanth:~$ sudo apt-get install -y gawk
```

Press enter to download the packages and install them.

### __Usage of Awk__

#### **1. Awk operations**
- Scans a file line by line
- Splits each input line into a field
- Compares input line/fields to pattern
- Performs actions on matched line. 

#### **2. Transform data files**

#### **3. Produce formatted reports**

#### **4. Programming Constructs**

- Format output lines.
- Arithmetic and string operations
- Conditionals and loops.
 
 ### __Syntax and Options__

_Syntax_

```bash
vasanth@vasanth:~$ awk options program file
```

_Options_

**-F fs** To specify a file separator.

**-f file** To specify a file that contains an awk script.

**-v var=value** To declare a variable.

 ### **Example :1**

```bash
vasanth@vasanth:~$ who | awk '{ print $1, $4 } '
dave 16:33
mary 10:34
eric 10:37
vasanth@vasanth:~$
```

 ### **Example :2**
```bash
vasanth@vasanth:~$ cat myfile.txt
This is the first text
This is a second text
This is the third text
This is the fourth text
vasanth@vasanth:~$ awk {'print $1'} myfile.txt
This
This
This
This
vasanth@vasanth:~$ 
```

### **Example :3**
```bash
vasanth@vasanth:~$ date
Saturday 21 August 2021 12:04:23 PM IST
vasanth@vasanth:~$ date | awk '{print $2,$3,$6}'
21 August PM
vasanth@vasanth:~$
```

#### **Explaination**
- **$0**  : Represents the entire line of the text.
- **$1**  : Represents the first field.
- **$2**  : Represents the second field.
- **$3**  : Represents the third field.
- **$5**  : Represents the fivth field.
- **$50**  : Represents the fifty field.
- **$NF**  : Stands for "number of field" and represent the last field.

### **Example :4**
```bash
vasanth@vasanth:~$ echo "Hello kumar" | awk '{$2="vasanth"; print $0}'
Hello vasanth
vasanth@vasanth:~$
```
#### **Explaination**
The first command makes the second field equals vasanth. The second command prints the entire line.

### **Example :5**
Print the file name and the number of lines.
```bash
vasanth@vasanth:~$ awk 'END { print "File", FILENAME, "contains", NR, "lines." }' teams.txt
File teams.txt contains 5 lines.
vasanth@vasanth:~$
```
#### **Explaination**
AWK has some built-in variables that contain useful information and allow you to control how the program is processed. The most common built-in variable here.
1. NF - The number of fields in the record.
2. NR - The number of the current record.
3. FILENAME - The name of the input file that is currently processed.
4. FS - Field separator.
5. RS - Record separator.
6. OFS - Output field separator.
7. ORS - Output record separator.

### **Example :6**
Print the file name and the number of lines.
```bash
vasanth@vasanth:~$ awk '{ sum += $3 } END { printf "%d\n", sum }' teams.txt
300
vasanth@vasanth:~$
```
#### **Explaination**
This command calculates the sum of values stored in the third field in each line.

### **Example :7**
Print the file name and the number of lines.
```bash
vasanth@vasanth:~$ awk -F: '$3 >= 1000 {print $1,$6}' /etc/passwd
nobody /nonexistent
vasanth /home/vasanth
vasanth@vasanth:~$ 
```

#### **Explaination**
 Print action only when the third field contains a value of 1,000 or greater:

 ### **Example :8**
```bash
vasanth@vasanth:~$ awk 'BEGIN { print sqrt((2+3)*5)}'
5
vasanth@vasanth:~$ 
```

#### **Explaination**
Functions can accept expression as a parameters.

### **Example :9**
```bash
vasanth@vasanth:~$ awk 'BEGIN { for (i = 1; i <= 7; i++) print int(101 * rand()) }'
28
58
54
45
22
34
82
vasanth@vasanth:~$ 
```

#### **Explaination**
Print seven random number.

### **Example :10**
```bash
vasanth@vasanth:~$ num=51 awk -v n="$num" 'BEGIN {print n}'
51
vasanth@vasanth:~$ 
```

#### **Explaination**
The shell variable in awk programs is to assign the shell variable to an awk variable.


-----

## SED

Sed stands for _**Stream editor**_ and is used to perform on file like, searching, find and replace, insertion or deletion operations.  Though most common use of the SED command in UNIX is substitution or find and replace.

Sed was developed from 1973 to 1974 by **Lee E. McMahon** of Bell labs.

### __Structure of SED__

![Workflow](https://www.tutorialspoint.com/sed/images/sed_workflow.jpg)

#### **1. Read**

SED reads a line from the input from stream (file, pipe, or stdin) and stores it in its internal buffer called **pattern buffer**.

#### **2. Execute**

All SED commands are applied sequentially on the pattern buffer. SED commands are applied on lines globally unless line addressing is specified.

#### **3. Display**

Send the modified contents to the input stream. After sending the data, the pattern buffer will be empty.
The above process repeats until the file is exhausted.

### **Installation from Source Code**
SED source code is available for free. The following installation applies to any GNU/Linux software.

__1. Download__

Download the source code from an authentic place. The command-line utility wget serves this purpose.

```bash
vasanth@vasanth:~$ wget https://ftp.gnu.org/gnu/sed/sed-4.2.2.tar.bz2
````

__2. Decompress and extract the downloaded source code__

```bash
vasanth@vasanth:~$ tar xvf sed-4.2.2.tar.bz2 
```
__3. Change into the directory and run configure__
```bash
vasanth@vasanth:~$ ./configure 
```
__4. Upon successful completion, the configure generates Makefile. To compile the source code, issue a make command__

```bash
vasanth@vasanth:~$ make
```
__5. You can run the test suite to ensure the build is clean. This is an optional step.__
```bash
vasanth@vasanth:~$ make check 
````
__6. Finally, install the SED utility. Make sure you have superuser privilege__

```bash
vasanth@vasanth:~$ sudo make install 
```

Press enter to install. After the installation makes sure to check the version.
### __Command Line Options__

|    **Options** |    **Usage** |
|-------------   |-----------   |
|  --version     |Output version information and exit.|
|--help          |Display this help and exit.|
|    -n          |Suppress automatic printing of pattern space.|
|-e              |Add the script to the commands to be executed.|
| -f             |Add the contents of script-file to the commands to be executed.|
|-i |Edit files in place (makes backup if SUFFIX supplied).|
|-l              |Specify the desired line-wrap length for the `l' command.|
|-E,  -r         |Use extended regular expressions in the script.|
|-s              |Consider files as separate rather than as a single, continuous long stream.|
|-u              |Load minimal amounts of data from the input files and flush the output buffers more often.|
|-z              |Separate lines by NUL characters.|

### __Syntax__

```bash
sed [OPTION]... {script-only-if-no-other-script} [input-file]...  
```
```bash
vasanth@vasanth:~$ ls -l | sed -n -e '/^d/ p'
```

as the long-listing starts each line with the 'd' symbol if it is a directory, so this will only print out
those lines that start with a 'd' symbol.

### **Example :1**
`sed` command can be used to substitution any part of a file content also. Create a text file named weekday.txt with the following content.

```bash
vasanth@vasanth:~$ weekday.txt
```

1. Monday
2. Tuesday
3. Wednesday
4. Thursday
5. Friday
6. Saturday
7. Sunday

```bash
vasanth@vasanth:~$ cat weekday.txt
```

```bash
vasanth@vasanth:~$ sed 's/Sunday/Sunday is holiday/' weekday.txt
```
**Output**

"Sunday" exists in the weekday.txt file and this word is replaced by the text, "Sunday is a holiday" after executing the above `sed` command.

```bash
vasanth@vasanth:~$ cat weekday.txt
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
vasanth@vasanth:~$ sed 's/sunday is a holiday' weekday.txt
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday is holiday
vasanth@vasanth:~$ 
```
### **Example :2**
Replacing words.
```bash
vasanth@vasanth:~$ sed 's/Kumar/Vasanth/g' example.txt
```

#### **Explaination**
Replace every occurrence of Kumar with Vasanth in example.txt

### **Example :3**

```bash
vasanth@vasanth:~$ sed -n 12,18p file.txt
```

#### **Explanation**
It shows only line 12 to 18 of the file.

### **Example :4**
```bash
vasanth@vasanth:~$ sed '$d' file.txt
```

#### **Explanation**
Delete the last line of the file.

### **Example :5**
print all lines except the first line.
```bash
vasanth@vasanth:~$ sed -n '1!p' filename
```
#### **Explanation**
! is used to apply commands on all lines except those who are specified before! symbol.

### **Example :6**
Add a line after/before the matched search
```bash
vasanth@vasanth:~$ sed '/danger/a "This is a new line with text after the match"' testfile.txt
```
```bash
vasanth@vasanth:~$ sed '/danger/i "This is a new line with text before the match" ' testfile.txt
```
#### **Explaination**
The first example to add a new line with some content after every pattern match, use the option ‘a’.

The second example is to add a new line with some content before every pattern match, use the option ‘i’.

### **Example :7**
```bash
vasanth@vasanth:~$ echo "Welcome To Our New Project" | sed 's/\(\b[A-Z]\)/\(\1\)/g'
(W)elcome (T)o (O)ur (N)ew (P)roject
vasanth@vasanth:~$ 
```
#### **Explaination**
This example prints the first character of every word in parenthesis.

### **Example :8**
```bash
vasanth@vasanth:~$ sed 's/|/~/g' file1.csv > file2.csv
```
#### **Explanation**
sed command that changes all pipe-delimited data of a file file1.csv to tilde delimited data, and save it to a file file2.csv

### **Example :9**
```bash
vasanth@vasanth:~$ sed '/^[[:space:]]*$/d' filename
```
#### **Explanation**
Remove the blank line from a file.

### **Example :10**
Appending line.
```bash
vasanth@vasanth:~$ sed -e 's/.*/ adding line using sed &/' testfile.txt
```
#### **Explaination**
To add some content before every line with sed So now every line will have 'adding line using sed’ before it.



-------

### **Reference**
AWK workflow : https://www.tutorialspoint.com/awk/awk_workflow.htm.

AWK Basics: https://en.wikipedia.org/wiki/AWK.

SED Basics: https://www.tutorialspoint.com/sed/sed_basic_commands.htm.

SED workflow: https://www.tutorialspoint.com/sed/pdf/sed_workflow.pdf.

SED installation: https://zoomadmin.com/HowToInstall/UbuntuPackage/gawk.