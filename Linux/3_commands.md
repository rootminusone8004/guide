# examples

``` bash
awk -F "/" '\^\// {print $NF}' /etc/shells | sort | uniq
```

`/` means the separator of columns is /  
`\^\//` means the lines startes with /  
`{print $NF}` means print the very last column  
`/etc/shells` is the file that keeps the shell names installed in the system

``` bash
df | awk '/\/dev\/sd/ {print $1"\t"$2 + $3}'
```

`df` is the command for displaying disk usage  
the regex is telling to use the lines having `/dev/sd` in them  
print the first column, give a tab and write the summation of second and third columns

``` bash
awk 'length($0) > 5' /etc/shells
```

print the lines that are geater then 5 chars.

``` bash
ps -ef | awk '{ if($NF == "/bin/fish") print $0}'
```

`ps -ef` shows all the processes  
if the last column is `/bin/fish` then print the entire line  
> `$0` means print the entire line

``` bash
awk 'BEGIN { for (i=1; i<=10; i++) print "the double of ", i, " is ", 2*i;}'
```

this command will print ten lines having a double value from 1 to 10.

``` bash
awk '$1 ~ /^[bc]/ {print $0}' .bashrc
```

this command will print out the lines that starts with `b` or `c` in the .bashrc

``` bash
awk '{print substr($0, 4)}' numbers.txt
```

This command will print every lines without **the first 4 characters**.

``` bash
awk 'match($0, /o/) {print $0 " has \"o\" character at " RSTART}' lol.txt
```

This command will check with char `o` and print out how far the first appearance of that char is.

``` bash
df | awk 'NR==7, NR==11 {print NR, $0}'
```

This command will print the lines from `7` to `11`.  
> **Note**: If you don't need line number, remove the NR, part in print

``` bash
awk 'END {print NR}' /etc/shells /etc/passwd
```

This command will count the total line numbers in both files and show the summation as output.
