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

 > sudo apt-get update -y

2. Step-2

>sudo apt-get install -y gawk

Press enter to download the packages and install them.


### __Versions and Implementations__

- BWK
- gawk
- mawk
- libmawk
- awka
- tawk
- Jawk
- xgawk
- QSEAWK
- libfawk
- BusyBox
- CLAWK

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

> $ awk options program file

_Options_

**-F fs** To specify a file separator.

**-f file** To specify a file that contains an awk script.

**-v var=value** To declare a variable.

 ### **Examples**

 > who | awk '{ print $1, $4 } '

![Example1](https://www.howtogeek.com/wp-content/uploads/2020/02/3-2.png?trim=1,1&bg-color=000&pad=1,1)

#### **Explainartion**
- **$0**  : Represents the entire line of the text.
- **$1**  : Represents the first field.
- **$2**  : Represents the second field.
- **$3**  : Represents the third field.
- **$5**  : Represents the fivth field.
- **$50**  : Represents the fifty field.
- **$NF**  : Stands for "number of field" and represent the last field.

> date

> date | awk '{print $2,$3,$6}'

![Example2](https://www.howtogeek.com/wp-content/uploads/2020/02/6-1.png?trim=1,1&bg-color=000&pad=1,1)

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

>  [vasanth]$ wget https://ftp.gnu.org/gnu/sed/sed-4.2.2.tar.bz2

__2. Decompress and extract the downloaded source code__

> [vasanth]$ tar xvf sed-4.2.2.tar.bz2 

__3. Change into the directory and run configure__

> [vasanth]$ ./configure 

__4. Upon successful completion, the configure generates Makefile. To compile the source code, issue a make command__

> [vasanth]$ make

__5. You can run the test suite to ensure the build is clean. This is an optional step.__

> [vasanth]$ make check 

__6. Finally, install the SED utility. Make sure you have superuser privilege__

> [vasanth]$ sudo make install 

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

>  sed [OPTION]... {script-only-if-no-other-script} [input-file]...  

>        ls -l | sed -n -e '/^d/ p'

as the long-listing starts each line with the 'd' symbol if it is a directory, so this will only print out
those lines that start with a 'd' symbol.

#### __Example__
`sed` command can be used to substitution any part of a file content also. Create a text file named weekday.txt with the following content.

>weekday.txt

1. Monday
2. Tuesday
3. Wednesday
4. Thursday
5. Friday
6. Saturday
7. Sunday

>$ cat weekday.txt

>$ sed 's/Sunday/Sunday is holiday/' weekday.txt

**Output**

"Sunday" exists in the weekday.txt file and this word is replaced by the text, "Sunday is holiday" after executing the above `sed` command.

![output](https://linuxhint.com/wp-content/uploads/2019/08/3-2.jpg)

-------

### **Reference**
AWK workflow : https://www.tutorialspoint.com/awk/awk_workflow.htm.

AWK Basics: https://en.wikipedia.org/wiki/AWK.

SED Basics: https://www.tutorialspoint.com/sed/sed_basic_commands.htm.

SED workflow: https://www.tutorialspoint.com/sed/pdf/sed_workflow.pdf.

SED installation: https://zoomadmin.com/HowToInstall/UbuntuPackage/gawk.