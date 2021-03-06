# 1.  introduction
 
  ## 1.1 reviewing Bash
   - **cat head tail more** *.txt
  ## 1.2 Tilde and Brace
   - **echo ~-** last directory
   - **touch** {a.txt, b.txt, c.txt}  
   - **touch** file_{1..10..2} 1 to 10 step of 2
   - **touch** file_{A..z..2} A to z step of 2
   - **ls -1| wc -l** count how many files
  ## 1.3 pipes and redirection
   - **ls |more**
   - **cp a b 1> success.txt 2> error.txt ** same as - **cp a b &> output.txt **
   - **1>** the success message
   - **2>** the error message
   - **&>** both success and error message
   - **ls > /dev/null** no print out
  ## 1.4 grep/awk/sed/cut
   - **grep  target file.txt** highline in the print out
   - **grep --color=auto target file.txt** use this if no highline in the print out
   - **export GREP_OPTIONS='--color=auto'** enable globally
   - **grep file.txt | awk {'print $2'}** only show the 2nd item from the pint out line
   - **ping abc.com |awk {'print $2'}**
   - **ping abc.com |cut -d= -f 4** delimiater on field 4 
   
# 2. Building Bash Script
  ## 2.1 echo 
  ```bash
     greeting="hello"
   echo \(hello\)             ( or ) special symbol needs \ before it to display
   echo '$greeting\(hello\)'  print out $greeting(hello)
   echo "\$greeting\(hello\)" print out $greeting(hello)
   echo "$greeting\(hello\)"  print out hello(hello)
  ```
  ## 2.2 variables
   - declare -i d=123      d is integer
   - declare -r e=456      e is read only
   - declare -l f="LofsD"  f is lofsd
   - declare -u g="LOdCat" g is LODCAT
   - **$HOME** home directory
   - **$PWD**  current directory
   -**MACHTYPE** machine type
   -**$HOSTNAME** system name
   -**$BASH_VERSION**
   -**$SECONDS** seconds bash session has been run (in the scrpit it star from zero)
   -**echo $0** return the name of the script
  ## 2.3 substitution
   ```bash
    a=$(ping abc.com |cut -d= -f 4)
    echo "The ping was $a"
   ```
  ## 2.4 numbers
   val=$(( expression ))  d=2 e=$((d+2))
   
   - primary use
   ```bash
    $a ** $b    exponentiation
    $a * $b     Multiplication
    $a / $b     division
    $a % $b     modulo
    $a + $b     addition
    $a - $b     subtraction
   ```
   - also able to use
   ```bash
    echo $e
    ((e++)) ,((e--)), ((e+=5)), ((e*=3))
    echo $e
    **NOTE e+=5** is a string operation e==>"4"+"5"==>"45" ,is not a number 
    
    float=$((1/3))             is 0
    float=$(echo 1/3 | bc -l)  too get the float point 
   ```
  ## 2.5 comparing values
    [[ expression ]] return 1/0 False/True
   - for char comparasion
   ```bash
   [[$a <  $b]]  less    than
   [[$a >  $b]]  greater than
   [[$a <= $b]]  less    than or equal to
   [[$a >= $b]]  greater than or equal to
   [[$a == $b]]                  equal
   [[$a != $b]]              not equal
   ```
   - for number comparasion
   ```bash
   [[$a -lt  $b]]  less    than
   [[$a -gt  $b]]  greater than
   [[$a -le $b]]  less    than or equal to
   [[$a -ge $b]]  greater than or equal to
   [[$a -eq $b]]                  equal
   [[$a -ne $b]]              not equal
   ```
   - logic operations
   ```bash
   [[$a &&  $b]]  AND
   [[$a ||  $b]]  OR 
   [[$a ! $b]]    NOT
   
   [[-z $a]]  is     null ?    
   [[-n $a]]  if not null ?
   ```
   
   - to use
   ```bash
   [["cat"=="cat"]] 
   echo $?
   [[20 -gt 100]]
   echo $?
   ```
   
   
   
   
   
   
   
