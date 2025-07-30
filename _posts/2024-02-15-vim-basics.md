---
layout: post
title: VIM Basics
date: 2024-02-15 16:30:00
categories: ["Technology","VIM"]
Tags : ["technology", "vim"]
---

Hi just an intro to VIM (Terminal Editor Application)
![Real Programmers](https://imgs.xkcd.com/comics/real_programmers.png)

## Basics that I know

Open Vim in Terminal ```vim``` or ```vim {filename} ```

How to save and Quit ```:wq```

## Indentation
- For Properly Indenting code use (place curser on line that needs to indented) ``` = = ```
- Visually Select and indent using ``` = = ```
- To indent the line to the right press ```>```
- To indent the line to the left press ```<```

## Multi-inserting same text in different lines 
- If you want to add the same word to multiple lines use visual block mode ```ctrl + v``` and then press ```shift + I``` and enter the text you want to type in and press ```esc```

## Macro Recordings
- Press ```q``` and then another key to start recording. The macro will be saved to the key that desired to press after the ```q```
- Press ```q``` again to stop macro recording
- Press ```@ + your-key``` to perform your recorded macro


## Finding Characters in a file
- Press ```f``` and then the letter you wish to find in that specific line that your cursor is on.(Even spaces ' ' can be find)

## Easy Movements across brackets
- Press ```%``` to find the end of brackets if you are in a block of function and repeat again to find the start of brackets.

## Joining Multiple lines
- Visually select the lines that you want to join and press ```J```

## Formatting Upper and Lower Case letters
- If you want to toggle a case of a character press ```~```
- To make a word upper case press ```gUw``` all at once and to make it lower case press ```guw```
- To make the entire line upper case ```gUU``` and lower case by ```guu```

## Increment a Number
- To make the number increment place the cursor on top of the number and press ```ctrl+a```
- To decrement the number press ```ctrl+x```

## Sorting a full text file
- type ```:sort``` to make the entire file sorted
- To make it entire sorted uniquely type ```:sort u```
- Sort in descending type ```:sort!```

## Read Content from external File
- To print the content of external file to the file that you are currently editing type ```:read <file-name>```
- To print the content of external commands (like ls,pwd,etc..) type ```:read !<command>```

## Substituting in vim
- To find and replace a word in vim type ```:s/<old-text>/<new-text>/g``` [here g means global]
- To delete line that matching the specific word ```g/<word-to-be-found>/d```
- To sort a comma seperated three column content in a file ```:%s/\(.*\),\(.*\),\(.*\)/\2,\1,\3/g```

## Registers in vim
- To get the registers list type ```:reg```
- To paste from a specific register use ```"<name-of-reg>pe```
- To keep in mind that ```"+``` reg is used for clipboard
- To save a text to a particular register use ```"<name-of-reg>y```
   
## Deletion in vim
- To delete a word type ```dw```
- To delete inside a word use ```diw```
- To delete around a word use ```daw```
- To delete whole line use ```dd```
- To select and delete bunch of lines then visually select and use ```dd```

## Copying in vim
- To copy a word type ```yw```
- To copy inside a word use ```yiw```
- To copy around a word use ```yaw```
- To copy whole line use ```yy```
- To select and copy bunch of lines then visually select and use ```yy```

> More will be Updated soon

{% include comment.html %}
