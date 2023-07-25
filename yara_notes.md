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
- If the *does not* exist, Yara will output an error:
```
marty@icebox: ~$ yara myfirstrule.yar somefile1111
error scanning somefile1111: could not open file
```
---
#### Expanding on Yara
- Yara writing rules link https://yara.readthedocs.io/en/stable/writingrules.html
- Above is some Yara documentation on writing rules in Yara. Big page could be useful to refer to when writing rules of your own.

##### Meta
- This section of a Yara rule is reserved for descriptive info by the author of the rule (think comments in python). For example, you can use ```desc```, short for description, to summarize what your rule checks for. Anything within this section does not influence the rule itself.

##### Strings
- As mentioned in the previous section, you can use strings to search for specific text or hexadecimal in files or programs. For ex, say we wanted to search a directory for all files containing "Hello World!",
```
rule helloworld_checker{
    strings:
        $hello_world = "Hello World!"
}
```
- We define the keyword ```strings``` where the string we want to search, i.e., "Hello World!" is stored within the variable ```$hello_world```. 
- However, we are missing a condition here to make the rule valid. For this example, to make this string the condition, we need to use the variable's name.
```
rule helloworld_checker{
    strings:
        $hello_world = "Hello World!"
        
    condition:
        $hello_world
}
```
- Basically, if any file has the string "Hello World!" then the rule will match. However, its only looking for this specific string so it will not match "hello world" or "HELLO WORLD".
- To solve this, the conditions ```any of them``` allows multiple strings to be searched for,
```
rule helloworld_checker{
    strings:
        $hello_world = "Hello World!"
        $hello_world_lowercase = "hello world"
		$hello_world_uppercase = "HELLO WORLD"

	condition:
		any of them
}
```
- Now any file with the strings "Hello World!" or "hello world" or "HELLO WORLD", will trigger the rule above.

##### Conditions
- Like regular programming, we can use comparison operators such as:
- <= less than or equal to
- \>= more than or equal to
- != not equal to
- For example:
```
rule helloworld_checker{
	strings:
		$hello_world = "Hello World!"

	condition:
        #hello_world <= 10
}
```
- The rule above will 1) look for the "Hello World!" string and 2) only say the rule matches if there are less than or equal to ten occurances of the "Hello World!" string.

##### Combining Keywords
- Additionally, you can use keywords like:
- **and**, **not**, **or**
- These keywords can be used to combine multiple conditions like if you wanted to check if a file has a string and is of a certain size
```
rule helloworld_checker{
	strings:
		$hello_world = "Hello World!" 
        
        condition:
	        $hello_world and filesize < 10KB 
}
```
#### Yara Modules
- **Cuckoo Sandbox** is an automated malware analysis enviroment. With this module you can generate Yara rules based upon the behaviors discovered from the Cuckoo Sandbox. As the sandbox executes malware, we can create rules on specific behaviors such as runtime strings and the like.
- **Python's PE** module allows you to create Yara rules from the various sections and elements of the Windows Portable Executeable (PE) structure. Examining a PE file's contents is an essential technique in malware analysis; behaviors such as cryptography or worming can be largely identified without reverse engineering or execution of the sample.

#### Yara Tools
- https://github.com/InQuest/awesome-yara
-- Github collection of Yara tools and resources. Huge.

- https://github.com/Neo23x0/Loki LOKI: a free open-source IOC scanner.
-- LOKI's detection is based on 4 methods: 1) File Name IOC Check 2) Yara Rule Check 3) Hash Check 4) C2 Back Connect Check

- https://www.nextron-systems.com/thor-lite/ THOR-Lite: a multiplatform IOC and Yara scanner. Features scan throttling to limit exhausting CPU resources. (Need to subscribe to their mailing list/register to download)

- https://github.com/Neo23x0/Fenrir FENRIR: a simple IOC scanner bash script. It allows scanning Linux/Unix/OSX systems for IOCs.

- https://github.com/Neo23x0/yarGen yarGen: a generator for Yara rules

