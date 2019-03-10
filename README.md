# Plain-text tools:head, tail, less, ls, cut, sort, uniq, diff, comm, join, grep, sed, awk

## head, tail, less:
    head -n <number> <file>
    tail -n <number> <file>
### the top/last num (默认为10) of the file

### 这两个函数还可以用来chop，如下：

    (head -n 2; tail -n 2) < Mus_musculus.GRCm38.75_chr1.bed
    
#### 然而，更robust的方法是使用 grep。

### less 命令的作用：1）检查文本；2）在 pipes 工作中 debbuging 和节省电脑运行，例如step1 input.txt | step2 | step3 > output.txt可以这样运行：

    step1 input.txt | less
    step1 input.txt | step2 | less
    step1 input.txt | step2 | step3 | less
    
## wc (word count), wc outputs the number of lines, words, and characters of the supplied file. 

    wc -l #return the number of lines

## ls -l reports file sizes in bytes， If we wish to use human-readable sizes, we can use ls -lh.

## cut 用来extract specific columns from the original file or stream：

    cut -f<num1,num2...>    
    cut -f num1-numx
    
## column program column -t (the -t option tells column to treat data as a table):

    column -t
    
### Note that you should only use columnt -t to visualize data in the terminal, not to reformat data to write to a file, but just make it easier to read.

## sort:

    sort -k2 # to sort based on the 2nd column
    sort -m # to sort more humanized, like 2 is placed before 10
    sort -r # to sort reversely
    
## diff file1 file2

#### "|"表示前后两个文件内容不同
#### “<"表示后面文件比前面文件少了1行内容
#### ”>“表示后面文件比前面文件多了1行内容

## grep

### grep -v 的注意事项（排除partial match)：

    $ cat example.txt
    bio
    bioinfo
    bioinformatics
    computational biology
    $ grep -v bioinfo example.txt
    bio
    computational biology
    $ grep -v -w bioinfo example.txt
    bio
    bioinformatics
    computational biology
    
# Decoding Plain-Text Data: hexdump

## 查看是ASCII还是UTF-8还是其他：

    file <file>
    
## 用 hexdump 或 grep 查看 non-ASCII characters, which can lead to problems:

    hexdump -c <file>
    
## uniq :Unix’s uniq takes lines from a file or standard input stream, and outputs all lines with consecutive duplicates removed.    

### Both sort | uniq and sort | uniq -c are frequently used shell idioms in bioinformatics and worth memorizing.



    
   
   



    
