# Emacs tutorial

不安装任何插件打开 Emacs, 比如在 Shell 中运行命令 emacs -nw -Q
M-x help-with-tutorial 打开教程
M-x describe-variable, 快捷键 C-h v, 查看变量的文档
M-x describe-function, 快捷键 C-h f, 查看命令的文档
M-x describe-key, 快捷键 C-h k, 查看快捷键的文档

M-x help-with-tutorial

```bash
# end the emacs session
C-x C-c 

# to quit a partially entered command
C-g

# view next screen
C-v

# move backwards on screen
M-v

# Clear screen and redispaly all the text
C-l

# moves to the beginning of the whole text
M-<

# moves to the end of the whole text
M->

# give arguments to command
C-u <num>

## windows
C-x 1 # kill all other windows

# move the cursor to this line and 
C-u 0 C-l

# display documentation on the C-f command
C-h k C-f

# undo,C+_ some terminals

C-/ 
C-_
C-x u
```

C-f     Move forward a character
C-b     Move backward a character

M-f     Move forward a word
M-b     Move backward a word

C-n     Move to next line
C-p     Move to previous line

C-a     Move to beginning of line
C-e     Move to end of line

M-a     Move back to beginning of sentence
M-e     Move forward to end of sentence


## deleting

```bash
## delete

        <DEL>       #  Delete the character just before the cursor
        C-d         # Delete the next character after the cursor

        M-<DEL>      # Kill the word immediately before the cursor
        M-d        #  Kill the next word after the cursor

        C-k         #  Kill from the cursor position to end of line
        M-k        #  Kill to the end of the current sentence
        
        # It reinserts the last killed text，yangking
        # If you do several C-k's in a row, all of the killed text is saved together, so that one C-y will yank all of the lines at once.
        C-y
        
        M-y
        
```

 You can also kill a segment of text with one uniform method.  Move to
 one end of that part, and type C-<SPC>.  (<SPC> is the Space bar.)
 Next, move the cursor to the other end of the text you intend to kill.
 As you do this, Emacs highlights the text between the cursor and the
 position where you typed C-<SPC>.  Finally, type C-w.  This kills all
 the text between the two positions.

The difference between "killing" and "deleting" is that "killed" text
can be reinserted (at any position), whereas "deleted" things cannot
be reinserted in this way (you can, however, undo a deletion--see
below).

## file&buffer

C-x C-f   Find a file
C-x C-s   Save the file
C-x C-b   List buffers
C-x 1 to get rid of the buffer list.
C-x b command.

## EXTENDING THE COMMAND SET

There are many, many more Emacs commands than could possibly be put
on all the control and meta characters.  Emacs gets around this with
the X (eXtend) command.  This comes in two flavors:

C-x     Character eXtend.  Followed by one character.
M-x     Named command eXtend.  Followed by a long name.

**Named eXtended commands are commands which are used even less
frequently, or commands which are used only in certain modes**
**replace-string.  Just type "repl s<TAB>" and
Emacs will complete the name**

C-x C-c offers to save each changed file before it kills Emacs.
C-z is the command to exit Emacs *temporarily*
auto-save
M-x recover-file <Return>

## mode

```bash
# is a command to switch to Fundamental mode.
M-x fundamental-mode  

# To view documentation on your current major mode, type
C-h m  

# You can turn Auto Fill mode.
M-x auto-fill-mode <Return> 

# The margin is usually set at 70 characters, but you can change it with the
C-x f 
```

If you make changes in the middle of a paragraph, Auto Fill mode
does not re-fill it for you.
To re-fill the paragraph, type M-q (META-q) with the cursor inside
that paragraph.

## searching

C-s  # for forward search
C-r  # for reverse search

## MULTIPLE WINDOWS

``` bash
## Move the cursor to this line and type .
C-l C-l

# to scroll other window.
C-M-v 

#  ("o" for "other") to move the cursor to the bottom window
C-x o
```

You do not have to display the same buffer in both windows.  If you
use C-x C-f to find a file in one window, the other window does not
change.  You can find a file in each window independently.

Here is another way to use two windows to display two different things:

Type C-x 4 C-f followed by the name of one of your files.
   End with <Return>.  See the specified file appear in the bottom
   window.  The cursor goes there, too.

Type C-x o to go back to the top window, and C-x 1 to delete
   the bottom window.
   
## MULTIPLE FRAMES

```bash
 #  See a new frame appear on your screen.
 M-x make-frame <Return>

 # This removes the selected frame.
 M-x delete-frame <Return>
```   

## recursive editing level

Type M-x to get into a minibuffer; then type <ESC> <ESC> <ESC> to  get out.

## GETTING MORE HELP


To use the Help features
`C-h character `

(If C-h does not display a message about help at the bottom of the
screen, try typing the F1 key or M-x help <Return> instead.)

hen Emacs displays a very brief description of the command.
`C-h c C-p`

This displays the documentation of the function
`C-h k C-p`

`C-h f`        Describe a function.  You type in the name of the function.

C-h v displays the documentation of variables

`C-h a`
Command Apropos.  Type in a keyword and Emacs will list
                all the commands whose names contain that keyword.
                These commands can all be invoked with META-x.
                For some commands, Command Apropos will also list a one
		or two character sequence which runs the same command.

Type C-h a file <Return>

This displays in another window a list of all M-x commands with "file"corresponding command names (such as C-x C-f beside find-file).

C-h i

Read included Manuals (a.k.a. Info).  This command puts
		you into a special buffer called "\*info\*" where you
		can read manuals for the packages installed on your system.
		Type m emacs <Return> to read the Emacs manual.
		If you have never before used Info, type ? and Emacs
		will take you on a guided tour of Info mode facilities.
		Once you are through with this tutorial, you should
		consult the Emacs Info manual as your primary documentation.

C-h r meacs manual


