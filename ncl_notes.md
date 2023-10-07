# Note Space for NCL challenges

## Enum and Exploit
#### Chall1
- "We have created a python script for you to break into as training. See if you can figure out a password that will authenticate with the program."
- "What is an input to this program that will result in a correct validation?"
```
#!/usr/bin/python

import sys

def main():
  if len(sys.argv) != 2:
    print("Invalid args")
    return
  password = sys.argv[1]
  builder = 0
  for c in password:
    builder += ord(c)
  if builder == 1000 and len(password) == 10 and ord(password[1]) == 83:
    print("correct")
  else:
    print("incorrect")

if __name__ == "__main__":
  main()
```
- If we enter a single argument in this program we will get an "Invalid args" output. The first part of the program checks for this (len(sys.argv != 2:)). However if we enter anything after the program in the cmd line we get incorrect, which is a step in the right direction. Another clue is the password variable (sys.argv[1]) as we can see that the password will be equal to some argument we enter.
- The next part I noticed is the for loop. It's using the ord function to count the unicode values of the characters we enter in our password. The first thing it checks for is if all the characters add up to 1000 and only 1000. Next it is checking if the password length is 10 characters. Finally, the loop is checking if the second character in the password we entered has the unicode value of 83. If we enter a password meeting all 3 of these criteria we will get a correct output.
- Searching for unicode characters online we can find that the unicode value of 83 is "S". We can also do this within the terminal using python. The chr method is the inverse of the ord method and will convert an integer to its unicode character and return it. For example the ```chr(83)``` returns "S". Now that we have this character we have the first part of our password. '_S______'.
- Since we know the value of 'S' is 83, we can subtract this value from 1000 to help us narrow down the rest of the 9 characters and their values. 1000 - 83 = 917, which means that the other characters in the password need to add up to 917.
- We can try dividing 917 by 9 to hopefully give us the unicode value of the other 9 characters. 917 / 9 = 101.888888889. 
- From here if we use ```chr(101)``` in python, we are shown that this unicode value is actually the letter 'e'. Also doing the modulo command in python we get 917 % 9 = 8. For some reason the NCL adds 101 and 8 to get the unicode value of 109 which is 'm'. I however mulitplied 101 times 9 which gave me 909, I then added 83 to this and got 992 which is 8 characters short of 1000.
- However 101 * 8 is 808 and adding 83 to that gives us 891. If we subtract 1000 from this we get 109 and which is the unicode value of 'm.' This should statisfy the password requirement as 109(m) + 83(S) + 808(eeeeeeee) = 1000, the password length is 10 characters and the second character is "S" or 83 in unicode. If we try this we get 'correct!'