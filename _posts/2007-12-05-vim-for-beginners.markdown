---
layout: post
title: "VIM for beginners"
---

The first time I saw vi text editor was when I reached university. At the time, it seemed a little bit counterintuitive . 
I think it is a normal feeling to new vi users, even more, if you are, like I was, used to Windows and GUIs but make no mistake, 
there is a good reason for this 30-year old tool still be widely used by many of the best developers in the world. 
A few days ago, I was programming some rails application, while doing some changes to a few files,
I realized that I wasn't taking full advantage of vim, 
I couldn't do what I normally saw my teachers doing, like !indenting! a text with few keyboard shortcuts.
I spend some hours reading the vim help and realized how fantastic vim is! 
Now if you wanna try vi I will give some little tips, like a mini tutorial for vi/vim beginners.

For showing you the shortcuts I’ll use a similar notation to the used on vim help.
`<ESC><CTRL-v>5jI`
This means you press ESC key then you press Ctrl and “v” key simultaneous then you press the number 5 followed by the “j” key and finally you press “I”. 
I think you get the idea. If you can’t, vim isn’t for you!

First, Vim has something similar to a command line, 
when you press `<ESC>:` you will start writing commands at the bottom of the screen for example, :q is for quitting the program. 
Of course when I say something started with “:” like “:q” I’m expecting you to write that on the command line, not in your text, 
so if you are in insert mode you have to do something like this `<ESC>:q<ENTER>`
Well... now when talked about insert mode I introduced one more thing; the vi working modes!
When using vim, you can switch between different working modes, for example to insert text you should be on INSERT MODE, 
when selecting text you are on SELECTION MODE, you have also REPLACE MODE, VISUAL MODE, and more. 
Those operating modes give you ultrafast access to key commands that can edit, insert, and move text on-the-fly.

Here are some examples of commands:

Calling VIM:

    Vi                 Open vim with no file.
    vi PATH            Open PATH file with vim, if the file doesn’t exist create it.
    vi PATH +          Open the PATH file and focus cursor at end of file.
    vi PATH +10        Open file at line 10.
    vi PATH +/regedor  Open file with courser at the first occurrence of  the word “regedor”

Saving/Quitting VIM:

    :w                 Save
    :q                 Exit without saving
    :wq or : x or ZZ   Exit and save
    :w!                Force Save
    :q!                Force Quit
    :wq!               Force Save and Quit

Well this is good for beginners. For now I don’t have more time, I will set up a more complex tutorial with a few more advanced commands soon.
