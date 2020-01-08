# emacs手册查看
 
 ## chapter 1
 
 ### Entering Emacs

```bash
 emacs & # background
 C-h t (help-with-tutorial).
emacs foo.txt starts Emacs with a buffer displaying the contents of the file ‘foo.txt’.
inhibit-startup-screen is non-nil, Emacs does not display the startup screen
*scratch* which can be used to evaluate Emacs Lisp expressions interactively
 initial-buffer-choice to a string naming that file or directory,The value of initial-buffer-choice may also be a function (of no arguments) that should return a buffer which is then displayed. If initial-buffer-choice is non-nil, then if you specify any files on the command line, Emacs still visits them, but does not display them initially.
```

### Exiting Emacs

```
C-x C-c
Kill Emacs (save-buffers-kill-terminal). 
C-z
On a text terminal, suspend Emacs; on a graphical display, iconify (or “minimize”) the selected frame (suspend-frame).

If the value of the variable confirm-kill-emacs is non-nil, C-x C-c assumes that its value is a predicate function, and calls that function. If the result of the function call is non-nil, the session is killed, otherwise Emacs continues to run. One convenient function to use as the value of confirm-kill-emacs is the function yes-or-no-p. The default value of confirm-kill-emacs is nil.

If the value of the variable confirm-kill-processes is nil, C-x C-c does not ask for confirmation before killing subprocesses started by Emacs. The value is t by default.

To kill Emacs without being prompted about saving, type M-x kill-emacs.

C-z runs the command suspend-frame.
jobs 
fz <id>
```

## Fundamental Editing Commands

### Basic

#### insertin Text


C-j, which inserts just a newline
<DEL> = delete-backward-char

C-q (quoted-insert)

C-q followed by any non-graphic character (even C-g) inserts that character. For instance, C-q <DEL> inserts a literal ‘DEL’ character.
C-q followed by a sequence of octal digits inserts the character with the specified octal character code. You can use any number of octal digits; any non-digit terminates the sequence. If the terminating character is <RET>, that <RET> serves only to terminate the sequence. Any other non-digit terminates the sequence and then acts as normal input—thus, C-q 1 0 1 B inserts ‘AB’.

To use decimal or hexadecimal instead of octal, set the variable read-quoted-char-radix to 10 or 16

A few common Unicode characters can be inserted via a command starting with C-x 8.

#### changing the location of Point

C-f
Move forward one character (forward-char). 
<RIGHT>
This command (right-char) behaves like C-f, except when point is in a right-to-left paragraph (see Bidirectional Editing). 
C-b
Move backward one character (backward-char). 
<LEFT>
This command (left-char) behaves like C-b, except if the current paragraph is right-to-left (see Bidirectional Editing). 
C-n
<DOWN>
Move down one screen line (next-line). This command attempts to keep the horizontal position unchanged, so if you start in the middle of one line, you move to the middle of the next. 
C-p
<UP>
Move up one screen line (previous-line). This command preserves position within the line, like C-n. 
C-a
<Home>
Move to the beginning of the line (move-beginning-of-line). 
C-e
<End>
Move to the end of the line (move-end-of-line). 
M-f
Move forward one word (forward-word). See Words. 
C-<RIGHT>
M-<RIGHT>
This command (right-word) behaves like M-f, except it moves backward by one word if the current paragraph is right-to-left. See Bidirectional Editing. 
M-b
Move backward one word (backward-word). See Words. 
C-<LEFT>
M-<LEFT>
This command (left-word) behaves like M-b, except it moves forward by one word if the current paragraph is right-to-left. See Bidirectional Editing. 
M-r
Without moving the text on the screen, reposition point on the left margin of the center-most text line of the window; on subsequent consecutive invocations, move point to the left margin of the top-most line, the bottom-most line, and so forth, in cyclic order (move-to-window-line-top-bottom).
A numeric argument says which screen line to place point on, counting downward from the top of the window (zero means the top line). A negative argument counts lines up from the bottom (−1 means the bottom line). See Arguments, for more information on numeric arguments. 

M-<
Move to the top of the buffer (beginning-of-buffer). With numeric argument n, move to n/10 of the way from the top. On graphical displays, C-<HOME> does the same. 
M->
Move to the end of the buffer (end-of-buffer). On graphical displays, C-<END> does the same. 
C-v
<PageDown>
<next>
Scroll the display one screen forward, and move point onscreen if necessary (scroll-up-command). See Scrolling. 
M-v
<PageUp>
<prior>
Scroll one screen backward, and move point onscreen if necessary (scroll-down-command). See Scrolling. 
M-g c
Read a number n and move point to buffer position n. Position 1 is the beginning of the buffer. 
M-g M-g
M-g g
Read a number n and move point to the beginning of line number n (goto-line). Line 1 is the beginning of the buffer. If point is on or just after a number in the buffer, that is the default for n. Just type <RET> in the minibuffer to use it. You can also specify n by giving M-g M-g a numeric prefix argument. See Select Buffer, for the behavior of M-g M-g when you give it a plain prefix argument. 
M-g <TAB>
Read a number n and move to column n in the current line. Column 0 is the leftmost column. If called with a prefix argument, move to the column number specified by the argument's numeric value. 
C-x C-n
Use the current column of point as the semipermanent goal column for C-n and C-p (set-goal-column) in the current buffer. When a semipermanent goal column is in effect, those commands always try to move to this column, or as close as possible to it, after moving vertically. The goal column remains in effect until canceled. 
C-u C-x C-n
Cancel the goal column. Henceforth, C-n and C-p try to preserve the horizontal position, as usual.

ou can force these commands to move according to logical lines (i.e., according to the text lines in the buffer) by setting the variable line-move-visual to nil;

When line-move-visual is nil, you can also set the variable track-eol to a non-nil value. Then C-n and C-p, when starting at the end of the logical line, move to the end of the next logical line. Normally, track-eol is nil.

#### help

If you forget what a key does, you can find out by typing C-h k (describe-key), followed by the key of interest; for example, C-h k C-n tells you what C-n does.

The prefix key C-h stands for “help”. The key <F1> serves as an alias for C-h. Apart from C-h k, there are many other help commands providing different kinds of help.

#### blank lines

C-o
Insert a blank line after the cursor (open-line). 
C-x C-o
Delete all but one of many consecutive blank lines (delete-blank-lines).

####  Numeric Arguments

  M-5 C-n
  
## Important Text-Changing Commands


