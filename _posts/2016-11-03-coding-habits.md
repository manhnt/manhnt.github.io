---
layout: post
title: My coding habits
categories: programming_technique
---

# My Coding Habits

This is a list of small habits that I make to my self when I do coding.

I mostly write code in C, using Vim or Sublime Text as my primary text editors. So 
these habits may be applicable only to me and completely nonsense to anyone else.

The list begins:

- In order to remove all compiler warnings from my code, I usually put and `#error` 
at the end of my code, so the compiler will stop at the `#error` for me to see all 
the warning from my code above. Fix all those warnings before continue going.
 
- Enable the text editor to display all tab characters, and redundant spaces at 
the end of each line. I hate redundant spaces and tabs. And this also helps to avoid
ugly, inconsistent indentation.

- Align the code vertically for more readable. Example:

```
char node[32]       =  {'\0'};
char value[32]      =  {'\0'};
char attribute[32]  =  {'\0'};
int  instance       =  0;
int  index          =  0;
```

This can be achived by using some plugins for the text editors (e.g [AlignTab]
for Sublime Text)


(The list will be updated as new habits grow :D)

Please give your ideas, suggestion and your personal habits in the comment.


[AlignTab]: https://github.com/randy3k/AlignTab

