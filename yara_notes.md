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