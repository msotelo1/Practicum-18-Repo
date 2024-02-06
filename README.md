# Instructions  

## Practicum 18 - The Scanner Class<br>

### BACKGROUND<br>
***The Scanner Class***
<br>
Most programming languages refer to input from the keyboard
as *standard input*, and output to the screen as *standard
output*. In Java, the standard input is defined by an object
named `in` which is defined as part of the `System` class. 
<br><br>
The `System` class is part of the `java.lang` package. Classes
of the `java.lang` package are automatically imported into
all Java programs, so an import statement such as
`import java.lang.Scanner` is not needed. The String class
is also part of the `java.lang` package.
<br><br>
For a long time, the way to read input from the keyboard
was to directly make use of the standard input `in` of the
`System` class (i.e., `System.in`). However, the standard
input always reads what is entered as character input (either
as a String type or as an integer character code). Thus,
if the user where prompted to enter numerical value and they
entered `10`, it would be read as the characters `1` and `0`
which would need to be *converted* to an integer value.
Eventually, at the request of many teaching Java, the
`Scanner` class was introduced allowing for the reading of
input as any primitive type or String type.
<br><br>
`Scanner input = new Scanner(System.in);`
<br><br>
This statement creates a Scanner object that "wraps itself
around" the standard input `in`. There method of the Scanner
class read the input from the standard input and convert it
to the desired type,
<br><br>
`nextInt` - reads a sequence of digit chars until a blank or
end-of-line character found and converts to an integer value.
<br>
`nextDouble` - read a sequence of digit chars, with possible
decimal point) until a blank or end-of-line and converts
to a double value.
<br>
`next` - reads a sequence of characters until a blank or
end-of-line character found and returns as a String value.
<br>
`nextLine` - reads a complete line of characters, including
blanks, returning a String value containing all characters
on the line (except for the end-of-line character).

***CAUTION When Using the Scanner Class!***
You must be careful to consider exactly what characters are
being read when reading input. The end-of-line character is
a character like any other, except that it is not displayed.
The following is an example of problematic code,
<br>
```java
    Scanner input = new Scanner(System.in);

    System.out.print("Enter an age: ");
    int age = input.nextInt();
    
    System.out.print("Enter a name: ");
    String name = input.nextLine();

    System.out.println("Age = " + age);
    System.out.println("Name = "+ name);
```
Here is the output of this code,
<br>
```java
Enter an age: 50
Enter a name: Age = 50
Name = 
>
```
What happened here is that the line to read the
name entered,
<br><br>
`String name = input.nextLine();`
<br><br>
never gave the user a chance to enter anything.
Why? Because the line that read in `age` read all
the digits characters of the age until it found
a blank character or the end-of-line. In this case,
it found the end-of-line character and stopped
reading any more characters. Then, the line to 
read the name, `input.nextLine()`, will read any
remaining characters. Since the end-of-line
characters is remaining, it reads that before even
waiting for the user to enter again, and the
name is read as an empty string. To fix this, an
extra `nextLine()` statement can be used to "scan
past" the end-of-line character,
<br>
```java
    Scanner input = new Scanner(System.in);

    System.out.print("Enter an age: ");
    int age = input.nextInt(); // scans past end of line
    
    System.out.print("Enter a name: ");
```
<br>
Note in the above situation, there would not have
a problem if both input lines were reading integer
(or any numeric) values. That is because when the
second input saw the end-of-line character, it would 
scan past it looking for the first digit character,
reading digit characters until a blank or 
end-of-line character was again found.

### WHAT TO DO<br>
- `Update the code` to get the correct output (i.e.,
  echoing out what is entered).
- `Run the predefined tests` (click Tests icon in the left column under Tools) and correct any logic errors. 
