# Yara
#### *This is a note space for the Yara THM module.*
---

#### What is Yara?
- From THM, "... Yara can identify information based on both binary and textual patterns, such as hexadecimal and strings contained within a file."
-- Yara rules are frequently written to determine if a file is malicious or not, based upon the features - or patterns - it presents, such as Strings in programming languages. For example, we could write a Yara rule to search for "hello world" in every program on our operating system if we would like. 

#### Babby's First Yara Rule
- The proprietary language that Yara uses for rules is 'trivial' to pick up but hard to master. This is due to the rule you set being only as effective as your understanding of the patterns you wish to search for.
- Using a Yara rule can be simple. Every Yara command **requires two arguments to be vaild**, these are:
-- 1) The rule file we create
-- 2) Name of file, directory, or process ID to use the rule for
- Every rule must have a name and condition.
- For example, if we wanted to use "myrule.yar" on directory "somedirectory", we could use:
```
yara myrule.yar somedirectory
```
- Next we'll make a basic yara rule.
1) Make a file named "somefile" via ```touch somefile```
2) Create a new file and name it "myfirstrule.yar"
3) Open the "myfirstrule.yar" using a text editor and input the snippet below
```
rule examplerule {
    condition: true
}
```
- The **name** of the rule in this code snippet is ```examplerule```, where we have one condition - in this case, the **condition** is ```condition```. As mentioned above, every rule needs both a name and condition to be valid, thus this example rule we created is valid.
- This example rule simply checks to see if the file/directory/PID that we specify exists via ```condition: true```. If the file *does* exist, we would be given the output of ```examplerule```
``` 
marty@icebox: ~$ yara myfirstrule.yar somefile
examplerule somefile
```
- If the **does not** exist, Yara will output an error:
```
marty@icebox: ~$ yara myfirstrule.yar somefile1111
error scanning somefile1111: could not open file
```