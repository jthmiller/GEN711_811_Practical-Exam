# lab 3

how to find directories
1. pwd = print working directory

directories can contain files or folders

2. ls = list
ls ' = bumps to new line, waiting for other end of quote '
use ctrl+c to exit = used to cancel

3. cd shell_data
4. ls
ls -F = adds slashes st end of directories
man ls = manual, give operator manual for ls
q exits to command line
ls -lrth = directories and owners, creation date, permissions listed

5. cd untrimmed_fastq/
start with cd u then tab to autofill
in eh1223@ron untrimmed_fastq

6. ls
head S tab 7 or 8 tab.fastq
lists genome data in form of fastQ

to get out
1. cd ../
in eh1223@ron shell_data, one step out
../../ is two steps out
etc
cd ~ 
~ = shorthand for home directory
then cd DIRECTORY

rm = remove, equivalent to delete
anything not pushed to git will be deleted
$VARIABLE = takes to variable site
echo shows paths within VARIABLE

history = shows entire command history
bottom most recent, top oldest

grep = basically ctrlF, searches lines for specific things

^ = beginning of line
ex. grep '^@'
shows results with @ at beginning of line

head = shows first few lines of a file

ls *FILE
* = wildcard, anything works
only listed files after *

ws = word count
gives line #, word #, character #
ls /bin/LETTER* | wc -l
gives word count for files in /bin that start with LETTER
-l = lines

less = allows scrolling through files

What are 3 ways to change directories to your home directory from the  untrimmed_fastq directory?
1. cd ~
2. cd ../../../
3. cd $HOME
4. bonus = copy and paste

Do each of the following tasks from your current directory using a single ls command for each:
    - List all of the files in /bin that start with the letter ‘c’.
    - List all of the files in /bin that contain the letter ‘a’.
    - List all of the files in /bin that end with the letter ‘o’.

Start with the letter c ____ ls /bin/c* OR ls /bin/ | grep '^c'
Start with the letter a ____ ls /bin/a*
Start with the letter o ____ ls /bin/o*

# lab 4

### EXERCISE 1: NAVIGATION PRACTICE
Navigate to your untrimmed_fastq directory in one command
cd gen711-811/shell_data/untrimmed_fastq/
can access using ls *untrimmed_fastq

### EXERCISE 2: WILDCARDS
What would the output look like if the wildcard could *not* be matched? Compare the outputs

expect an error
ls: cannot access '*fq': No such file or directory

### EXERCISE 3: NAVIGATING PRACTICE
Navigate to your home directory. From there, list the contents of the untrimmed_fastq directory.

cd / cd $HOME / cd ~ = home directory
SRR907977.fastq
SRR098026.fastq
headliners.txt

### EXERCISE 4: FINDING HIDDEN DIRECTORIES
First navigate to the shell_data directory. There is a hidden directory within this directory. Explore the options for ls to find out how to see hidden directories. List the contents of the directory and identify the name of the text file in that directory.

Hint: hidden files and folders in Unix start with ., for example .my_hidden_directory

ls -a / ls --all = finding hidden directories
ls -Fa = all directories with a slash
ls -laF = shows domain, users, last edited or accessed

What is the hidden file name in the hidden directory?
youfoundit.txt

### EXERCISE 5: HISTORY
Find the line number in your history for the command that listed all the .sh files in /usr/bin. Rerun that command.

427  ls /usr/bin/*.sh
!# = rerun a specific code from history
/# = line number

### EXERCISE 6: FILE CONTENTS
Print out the contents of the ~/shell_data/untrimmed_fastq/SRR097977.fastq file. What is the last line of the file?
cat = prints whole file to screen

### EXERCISE 7: PATHS
From your home directory, and without changing directories, use one short command to print the contents of all of the files in the ~/shell_data/untrimmed_fastq directory.

### EXERCISE 8: LESS
What are the next three nucleotides (characters) after the first instance of the sequence quoted above?

CAC
less FILE NAME or less -S FILE NAME
use Shift+G to go to bottom and Q to exit
also use grep 'TTTTT' *fastq = 'TTTTT' can be replaced by anything within file (ex.nucleotide sequence)
head FASTQ to top
tail FASTQ to bottom
tail -n3 FASTQ gives last 3 lines

mkdir = make directory
cp = copy
cp SRR098026.fastq SRR098026-backup.fastq = copy fastq file
cp SRR098026.fastq /usr/SRR098026-backup.fastq = make copy from home directory
mv = move
mv *backup.fastq_backup/ = move everything that ends in backup.fastq to backup folder
mv *backup.fastq_backup backup = move fastq backup tp backup directory

-You can view file contents using `less`, `cat`, `head` or `tail`.
- The commands `cp`, `mv`, and `mkdir` are useful for manipulating existing files and creating new directories.
- You can view file permissions using `ls -l` and change permissions using `chmod`.
- The `history` command and the up arrow on your keyboard can be used to repeat recently used commands.

use clear to "erase" all data in terminal

echo = echoes everything back

# lab 5

- You can view file contents using `less`, `cat`, `head` or `tail`.
- The commands `cp`, `mv`, and `mkdir` are useful for manipulating existing files and creating new directories.

to read fastq files:
1. @SSR... is the first line that is succeeded by the sequence
@SRR097977.249 209DTAAXX_Lenski2_1_7:8:3:441:292 length=36
GGGTAGGTATTACTCAGGACGAGGCGGTCGTGCCAC

2. +SRR... is succeed by the quality score in charas, numbers, letters
+SRR097977.249 209DTAAXX_Lenski2_1_7:8:3:441:292 length=36
C:CCC::CCCCCCCC<8?6A:C28C<608'&&&,'$

3. tags and length should be identical
4. each quality score aligns to a base pair

chmod = change mode
removes privaleges to files
r = read 
w = write
x = execute
- = no permissions
chmod ug+rwx FILE NAME = allows read write execute to user and group
-rw-r--r--. 1 eh1223 domain users 47552 Feb 20 15:46 SRR097977.fastq_backup
to remove permissions: chmod -w FILE NAME

rm = remove
-R = recursive, goes inside folder
f = force, skips warning
rm -Rf backup/ = removes everything from and backup directory

exercise 1:
Make sure that you have deleted your backup directory and all files it contains.
rm -Rf backup/

Create a backup of each of your FASTQ files using cp
cp SRR097977.fastq SRR097977.fastq_backup
cp SRR098026.fastq SRR098026.fastq_backup

Use a wildcard to move all of your backup files to a new backup directory
mv *.fastq_backup backup

exercise 2:
Change the permissions on all of your backup files to be write-protected.
chmod -w SRR097977.fastq_backup
chmod -w SRR098026.fastq_backup

How do you know they are write protected?
A: w is replaced by -

everything so far has been bash/shell script
now moving onto conda

conda activate genomics = load genomics conda environment
conda deactivate = deactivates conda enviroment

fastqc -h = opens fastqc help menu, shows all available commands

fastqc *.fastq* = started analysis fastq files

which = shows where everything is installed

exercise 3:
where is the program 'fastqc' stored?
conda activate genomics
which fastqc

unzip = opens zip files

# lab 6

ls -lrth = lists everything in a directory by numerical order (date)
Ctrl + R, then begin typing what is being searched to find previous use
> = redirection to a location rather than another command
>> = write history to end of file, similar to word count
grep -v = inverse grep, removes matches and leaves good reads
'^' = indicates beginning of line

## Exercise 1

1. Search for the sequence `GNATNACCACTTCC` in the `SRR098026.fastq` file. 
grep -B1 GNATNACCACTTCC SRR098026.fastq
  Have your search return all matching lines and the name (or identifier) for each sequence
  that contains a match.
  GNATNACCACTTCCAGTGCTGANNNNNNNGGGATG

2. Search for the sequence `AAGTT` in both FASTQ files.
grep -B1 AAGTT *.fastq
  Have your search return all matching lines and the name (or identifier) for each sequence
  that contains a match.
GATTGCTTTAATGAAAAAGTCATATAAGTTGCCATG
TTGTCCACGCTTTTCTATGTAAAGTTTATTTGCTTT
TGAAGCCTGCTTTTTTATACTAAGTTTGCATTATAA
GTGGCGCTGCTGCATAAGTTGGGTTATCAGGTCGTT
GGCAAAATGGTCCTCCAGCCAGGCCAGAAGCAAGTT
TTTATTTGTAAAGTTTTGTTGAAATAAGGGTTGTAA
TTCTTACCATCCTGAAGTTTTTTCATCTTCCCTGAT

GNNNNNNNNCAAAGTTGATCNNNNNNNNNTGTGCG

3. How do the search results differ when matching in one file vs. both files? If you wanted to keep the original FASTQ format, how would you get around this? 

4. Make a file called 'bad-reads.fastq' made up of reads with 10 Ns or more in a row

## Exercise 2

How many sequences are there in `SRR098026.fastq`? Remember that every sequence is formed by four lines.
 grep '^@SRR' SRR098026.fastq -c
249

## Exercise 3

How many sequences in `SRR098026.fastq` contain at least 3 consecutive Ns?
grep 'NNN' SRR0908026.fastq -c
249

for loop = allows a command to be done over and over
for name in *.fastq
do
echo ${name}
done

# lab 7

- created groups and picked topic for final project
- created github repository "CYANOBACTERIA!!!"
- next step: need metadata, create directory in gen711?

special characters in metadata can create horrible issues, so avoid that shit like the plague
- no commas, no spaces, no tabs

viewed metadata (gen711 fork, lab 7, view metadata here link)

"curk -O LINK" to download files
use less to view txt files
- Q/Ctrl C to exit less

cut = remove something from a 

# practice-cal

### 1. Paste the command(s) below that you used get practical exam pasted into vscode. (2 point)
ctrl+a
ctrl+c
ctrl+v

### 2. From your home directory, make a new directory to hold fastq files called 'analysis' (2 points)
mkdir analysis

### 3. Copy the fastq files /tmp/gen711_2023/Sample1.fastq and /tmp/gen711_2023/Sample2.fastq directly into the 'analysis' directory without changing your current directory. (2 points, partial credit if you need to change directories first)
- this may not be possible; copy and paste from github, not pulled 
- note 3/25: LMAO IT IS POSSIBLE THANKS COPILOT

cp /tmp/gen711_2023/Sample1.fastq /tmp/gen711_2023/Sample2.fastq analysis/

cp = copy, requires absolute paths

For todays practice practical, use SRR fastqs instead
### 4. Use an absolute path to change your current working directory to the 'analysis' folder/directory. (2 points, partial credit for using a relative path)
cd /home/users/eh1223/gen711-811/analysis

### 5. The fastq file you just copied is data from the UNH genome center. This is the first time you've ever seen these FASTQs. To confirm that the format of the FASTQs look ok, view one of the two files and paste the top 4 lines of the file below. (4 points) 
head SRR097977.fastq
OR
head -n 4 SRR097977.fastq <- this is preferred
head = top of file
head -n 4 = top four lines
-n = tells head how many to show

@SRR097977.1 209DTAAXX_Lenski2_1_7:8:3:710:178 length=36
TATTCTGCCATAATGAAATTCGCCACTTGTTAGTGT
+SRR097977.1 209DTAAXX_Lenski2_1_7:8:3:710:178 length=36
CCCCCCCCCCCCCCC>CCCCC7CCCCCCACA?5A5<
@SRR097977.2 209DTAAXX_Lenski2_1_7:8:3:365:371 length=36
GGTTACTCTTTTAACCTTGATGTTTCGACGCTGTAT
+SRR097977.2 209DTAAXX_Lenski2_1_7:8:3:365:371 length=36
CC:?:CC:?CCCCC??C?:?C-&:C:,?<&*?+7?<
@SRR097977.3 209DTAAXX_Lenski2_1_7:8:3:663:569 length=36
TTGTTCGCTTTTGGTAATTAATCCCGGAAATAATAA

### 6. You've decided that you want to make a seperate file of the reads to BLAST them at NCBI to make sure they belong to the species that you seqiuenced. However, your blast program is written to accept FASTA files rather than FASTQ files (FASTA files only contain the header line above the read, and the read itself). You will need to make a 'FASTA' file from each FASTQ file. Before you make the new files, pipe the output to a command that that allows you to see just the first lines of the output. (5 points)  
grep --no-group-separator '^@SRR097977.1 ' SRR097977.fastq | head
OR
grep -A1 --no-group-separator "^@SRR.1 " SRR.fastq | head <- this is preferred, did not test other one

grep "^@SRR.1 " = matches header lines that begin with @
-A1 = print the matching line and 1 line after it, results in header and sequence
--no-group-separator = prevents grep from inserting spacers
| (pipe) head = shows first 10 lines

4/30:
also can use grep -A1 --no-group-separator '^@' FILE.fastq | head

#### Hints: 
### FASTA only needs 2/4 lines that are in a FASTQ: 1) the header line that starts with '@' and 2) the sequence right after the header. However, the base call quality scores could contain '@' as well, which might lead to unwanted matches. 
### You can use the info in the header line to be very specific about what you are trying to match. 
### Add the '--no-group-separator' option to the other options of your command to keep the '--' out of the output

### 7. Redirect the output of your command (command in 6 that is converting the format of the FASTQ into FASTA) into new files. Give the new file the same names, but uses the '.fasta' extension rather than the '.fastq' extension of the original file name. (5 points)
head -n 4 SRR.fastq > SRR.fasta
*> = creates or overwrites a file
*>> = adds to existing file

### 8. How many reads have 15 or more uncalled bases (NNNNNNNNNNNNNNN) in both samples? Count the number of reads in both WITHOUT making a new file. (4 points)
wc -l SRR.fastq
OR
grep -c "^@" SRR.fastq

wc = word count
wc -l (L) = word count for lines only

grep = print lines that matches pattern
-c = count
grep -c = counts lines that match pattern, outputs a number

4/30:
grep -B1 -A2 'NNNNNNNNNNNNNNN' FILE.fastq | grep -c '^@' 

grep -B1 -A2 = gives full 4-line FASTQ record
-c = counts reads

### 9. Make a new directory called 'to_blast' in your current directory. Then, move the two fasta files into this new 'to_blast' directory (4 points)
mkdir to_blast
mv FASTA1 to_blast
mv FASTA2 to_blast

4/30:
mv *.fasta to_blast

### 10. Without changing directories, what command could you use to confirm that the files made it into the 'to_blast' folder. (2 points)
ls PATH/TO/FOLDER
ex. ls shell_data/to_blast
OR
ls PATH/TO/FOLDER*.fastq OR *.fasta

4/30:
ls to_blast <- much easier and much fewer steps

### 11. What is the 100th line in the Sample1.fasta file? (hint: the 'head' command is one way to do this- but you may need to specify an option) (2 points)
head -n 100 Sample1.fasta | tail -n 1

head -n 100 = prints first 100 lines
tail -n 1 = takes the last line
| = a pipe, sends the output of command 1 directly into command 2
ex. head -n 100 prints 100 lines, | sends the 100 lines into tail, tail -n 1 prints the last line, results in line 100 exclusively

### 12. Run md5sum on Sample1.fasta (md5sum Sample1.fasta). Then, run it again, but redirect the output to a new file called 'my_md5sums.txt'.  (2 points)
md5sum = MD5 checksum, verifies file integrity and detects corruption

md5sum Sample1.fasta > my_md5sums.txt
*> = redirects output
my_md5sums.txt = file is created

cat = reads a file and prints contents
cat FILENAME.txt = view a vile
cat FILE1 FILE 2 = view files in order
cat FILE1.txt FILE2.txt > combined.txt = combines files into one new file
cat Sample1.fasta | grep "ANYTHING" = sends file contents into grep for searching

### 13. Next, run the md5sum command on Sample2.fasta and add it the the end of 'my_md5sums.txt'. (2 points)
md5sum Sample2.fasta >> my_md5sum.txt

### 14. Lastly, add your name to the end of 'my_md5sums.txt' file. (2 points)
echo "NAME" >> my_md5sums.txt

echo = used to produce text, this case a name
*>> = adds to end of  (asterisk not included but the alligators alone do a weird thing)

### Extra credit: Run fastqc on one of the fastq files, and one of the fasta files. Did they both run? Why or why not?  (2 points)
fastqc is specifically for raw sequences  that is stored in fastq format that includes quality scores
does not run with fasta bc it doesnt have quality scores

# bash commands
- https://phoenixnap.com/kb/bash-commands

ls = lists all files and directories in current directory
ls -a = shows hidden files in output

cd = changes current directory to directory specified
cd - = goes to previous directory
cd ~ = goes to home directory
- syntax: cd [directory]

pwd = prints path of current working directory
- syntax: pwd [options] or simply just pwd
ex. pwd -L or -P (but we didnt use these so whatever)

cat = displays contents of a file without opening the file
cat -n = numbers all output lines
- syntax: cat [options] [file path]
ex. cat -n (the option) file.txt

mkdir = creates a new, empty directory
- syntax: mkdir DIR NAME

rmdir = removes ONLY EMPTY directory
- syntax: rmdir DIR NAME

cp = copy files and directories
- syntax: cp [source (usually a file)] [destination (usually a directory)]

mv = move directories and files
- syntax: mv [source] [destination]

grep = searches files for lines that match a search pattern
- syntax: grep [options, like -c] ["search pattern'] [file]

head = allows preview of the beginning section of a file
head -n = shows the first n number of lines
- syntax: head [options] [file]

tail = displays the end of a file
tail -n = shows the last n number of lines
- syntax: tail [option] [file]

echo = displays text as standard output
- syntax: echo [option] [string]

| (pipe) = connects outputs of one command to the input of another command
- syntax: [command 1] | [command 2]

[>] = redirects output to a file
[>>] = adds outout to specified file
- syntax: [command] < [file]

gzip = compresses files
- syntax: [options] [file]
- options:
-d = decompresses a compressed file

gunzip = decompresses files

- https://ss64.com/bash/

wc = word count, prints byte, word, line counts
wc -c = prints byte counts
wc -w = prints word counts
wc -l = prints newline counts
wc -L = prints longest line of file
- syntax: wc [options] [file]

## Practical
---

1. Use an absolute path to change your current working directory to the 'prac_exam' directory that you just cloned (2 points). 
  
  cd /home/users/eh1223/prac_exam_2026
  
2. From 'prac_exam' directory, make the following directory structure in a single command: `data/untrimmed_fastq` (2 points, -1 point if you need to use 2 commands for this. Hint: There is a flag/option that lets you create nested directories all at once.)

mkdir untrimmed_fastq | mkdir data
mv untrimmed_fastq data

mkdir untrimmed_fastq/ data/ <- makes two separate directories
CORRECT: mkdir -p data/untrimmed_fastq
-p = allows for making parent directories

3. Copy the two fastq files in the `/tmp/Gen711-811_data` directly into your `untrimmed_fastq` directory without changing your current directory. (2 points, partial credit if you need to change directories first. Multiple correct answers)
  
cp -r /tmp/Gen711-811_data/ untrimmed_fastq DESTINATION
-r = recursive, copies folder, all files, all subfolders
OR
cp /tmp/gen711_2023/Sample1.fastq home/users/eh1223/DESIRED-DIRECTORY

4. List all the hidden files in this repo. Paste the command below (2 points)

ls -a

5. Use a relative path to change your current working directory to the `untrimmed_fastq` directory. (2 points)

cd /home/users/eh1223/prac_exam_2026/data/untrimmed_fastq <- this is an absolute path, relative path is dependent on current directory
if in [eh1223@ron prac_exam_2026], then cd data/untrimmed_fastq

6. These are paired-end FASTQ files from an *E. coli* long-term evolution experiment. To confirm the files look ok, view one of them and paste the top 4 lines below. (4 points, Hint: These files are gzip-compressed. Multiple correct answers)

gunzip SRR2584863_2.fastq.gz
head -n 4 SRR2584863_2.fastq


7. How large (file size) are the two uncompressed fastq files? Use a single command with appropriate options to show the file sizes in a human-readable format (e.g., MB). Paste the command and output below. (2 points)

545M for SRR2584863_2
972M for SRR2584866_2

CORRECT: ls -lrth = lists files oldest -> newest, with readable sizes
OR
ls -lh FILE NAME
-l = long listing (permissions, owner, size, timestamp)
-h = human readable
-r = reverses
-t = sort by modification time

8. For each fastq, how many quality score lines have the '@' symbol in them? To answer this, use one line of piped bash commands for each fastq, and the output should be a single number.(2 points) 

4067718
grep "@" SRR2584863_2.fastq | grep -v "^@" SRR2584863_2.fastq -c
i think this is CORRECT

9. How many reads have 15 or more uncalled bases (`NNNNNNNNNNNNNNN`) in `SRR2584863_2.fastq`? Count WITHOUT making a new file (4 points)

3015
grep "NNNNNNNNNNNNNNN" SRR2584863_2.fastq | wc -l

CORRECT: grep -B1 -A2 'N\{15\}' FILE.FASTQ | grep -c '^@'
'N\{15\}' = 15 or more
can also use "NNNNNNNNNNNNNNN"
-B1 = 1 before the sequence line
-A2 = 2 after the sequence line
-c = counts reads
if zipped: zgrep

10. Make a single fasta file from the two fastqs using the reads found in the question above, and their respective info lines. Name the new file 'badreads.fasta' in the 'untrimmed_fastq' directory.  (4 points)

Hint: the first 4 lines of badreads.fasta should look similar (but maybe not exactly) to this:
```
@SRR2584863.1 HWI-ST957:244:H73TDADXX:1:1101:4712:2181/2
GGCGACATTACTGACCCGCNNNNNNNNNNNNNNNNNNNCGACNNNNNNNNNNNNNNNNNCCTGATNNNNNNNNNNNNNNNTCAGNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNN
@SRR2584863.2 HWI-ST957:244:H73TDADXX:1:1101:8571:2191/2
TCCCCGGAGTCAGCAGGGTGNNNNNNNNNNNNNNNNNATACATNNNNNNNNNNNNNNNGTTTTTGNNNNNNNNNNNNNNGCTGTCNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNN
```
grep -B1 "NNNNNNNNNNNNNNN" SRR2584866_2.fastq > badreads.fasta

11. Activate the conda 'genomics' environment that contains `fastqc` and confirm where `fastqc` is installed. Paste the command and its output below. (2 points)

conda activate genomics
fastqc which

CORRECT: which fastqc
result should look like /user/local/bin/fastqc

12. Run `fastqc` on `SRR2584863_1.fastq`. Then, create a `results/fastqc_untrimmed_reads` directory and move both the `.zip` and `.html` output files into it — all without leaving your `untrimmed_fastq` directory. Paste all commands used. (4 points)

mkdir results
mkdir fastqc_untrimmed_reads
mv fastqc_untrimmed_reads/ results
mv SRR2584863_2_fastqc.html fastqc_untrimmed_reads
mv SRR2584863_2_fastqc.zip fastqc_untrimmed_reads

CORRECT: 
fastqc FILE.FASTQ
mkdir -p results/fastqc_untrimmed_reads
mv FILE_fastqc.* DESTINATION DIRECTORY/


13. Without changing directories, what is the 100th line of the file `SRR2584863_1.trim.fastq` in your `trimmed_fastq` directory? (2 points)

head -n 100 SRR2584863_2.fastq | tail -n 1


14. Run `md5sum` on `SRR2584863_1.fastq`. Then run it again, redirecting the output to a new file called `my_md5sums.txt`. Next, run `md5sum` on `SRR2584863_2.fastq` and **append** it to `my_md5sums.txt`. Finally, append your name to the end of `my_md5sums.txt`. Paste all commands used. (4 points)

CORRECT:
md5sum SRR2584863_2.fastq
md5sum SRR2584863_2.fastq > my_md5sums.txt
md5sum SRR2584866_2.fastq >> my_md5sums.txt
echo "ELIANA" >> my_md5sums.txt

---

# 01 trim
1. conda activate genomics
2. cd CYANOBACTERIA
3. polyg_len=200
4. chmod +x code/polyGfilter.sh
5. find data/poly-G-trimmed/ -size 0 -print -delete

# 02 cut-adapt
1. conda activate qiime2 amplicon 2026.1
2. determine primer and proj name 
primer = 16s_V4-V5
proj name = DEP_${primer}
3. qiime import
4. forward primer
5. reverse primer
6. cutadapt_config
7. qiime cutadapt parameters
8. qiime demux summarize

# 03 denoise
1. conda activate qiime2
2. determine primer and proj name
3. trunc
lenf=220
lenr=215
4. trim
leftf=0
leftr=0
5. thread
threads=1
6. qiime dada denoise paired