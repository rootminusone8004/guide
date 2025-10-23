# Regular Expression

A regular expression is a sequence of characters that specifies a match pattern in text. Usually such patterns are used by string-searching algorithms for **find** or **find and replace** operations on strings, or for input validation.

| symbol   | meaning                                               |
|----------|-------------------------------------------------------|
| .        | Any one character                                     |
| *        | Match any number of previous char (including 0 chars) |
| +        | Match any number of previous char (1 or greater)      |
| $        | end of the line                                       |
| ^        | begging of the line                                   |
| \S       | any non-whitespace character                          |
| \s       | any whitespace character                              |
| ?        | optional character                                    |
| \        | escape something                                      |
| [a-z]    | any lowercase char                                    |
| [A-Z]    | any uppercase char                                    |
| [A-Za-z] | any character                                         |
| [3-9]    | digits from 3 to 9                                    |

Some expressions are given below.

| expression | words eligible                        |
|------------|---------------------------------------|
| car        | car, cars, scar, oscar, scary         |
| f.x        | fox, fix, fax, crucifixion            |
| f.*x       | fox, fix, fax, fooooooooox, fx, faaax |
| f.+x       | fox, fix, fax, fooooooooox, faax      |
| x$         | fox, fix, regex, doxx, six            |
| ^sp        | split, splinter, sparse, spring       |
| \S*oomer   | boomer, zoomer, consoomer             |
| \s+umer    | the consumer, the        lumer        |
| http?      | http, https, httpd                    |