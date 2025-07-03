# Activity 2: Shell Games

### July 1, 2025

### Skiers (John Chin, Ian Olson)

1.  **What does that pattern mean?**  
    The pattern `[["$num" =~ ^[+-]?[0-9]+(\.[0-9]+)?$]]` checks if ‘num’ is a valid number. Step by step, it sees if num ‘matches the pattern’ (=~) of the negation of the regular expression that starts with zero or one instances of a + or - sign, is followed by one or more instances of a valid digit (0-9), and optionally ends with a decimal point followed by any valid digit. $ signifies end of line.

2.  **Test the shell script to see if it works. Can you break it?**  
    It works most of the time but I can break it. I enter the number: +3. Then it gives me a syntax error and goes haywire from there.

3.  **When the user enters CTRL-D, the final message comes out on the last prompt line. How could you fix that?**  
    If you're fine with having the last prompt line, but just want to move the final message to a new line, you could change the final echo command to have a new line: `echo -e "\nThe sum of the numbers is: $sum"`.

4.  **While the script works with negative numbers (e.g., -3) it fails for numbers entered with a leading + sign, even though the pattern accepts them. Why does it fail on +3?**  
    Not sure, but does it have do with the fact that + is one of the metacharacters for regex elements in bash?

5.  **How would you modify the script to handle subtraction in addition to addition?**  
    You could modify the code to be like this:
    #!/bin/bash

        sum=0
        prev=0
        action="adding"
        echo "Enter numbers to calculate their sum (Ctrl+D to finish):"

        while read -p "Enter a number: " num; do
            # Check if the input is a valid number
            if [[ "$num" =~ ^[+-]?[0-9]+(\.[0-9]+)?$ ]]; then
                echo "$action"
                if [[ "$action" == "adding" ]]; then
                    sum=$(bc <<< "$sum + $num")
                elif [[ "$action" == "subtracting" ]]; then
                    sum=$(bc <<< "$sum - $num")
                fi
            elif [[ "$num" == + ]]; then
                echo "adding!"
                action="adding"
            elif [[ "$num" == - ]]; then
                echo "subtracting!"
                action="subtracting"
            else
                echo "Invalid input. Please enter a valid number."
            fi
        done

        echo -e "\nThe sum of the numbers is: $sum"

6.  How would you modify the script to display the current total in every prompt?  
    You could add a line after the do statement and before the if statements:

        while read -p "Enter a number: " num; do
        echo "current total is: " $sum

7.  Rewrite the script to take ALL the numbers and operations as a single input and display the result.

    This was pretty hard.
