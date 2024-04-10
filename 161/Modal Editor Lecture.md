# Quiz Stuff
- What are they?
- Common modes
- Why would you use a modal editor?
# what's a modal editor
- Text editor that have different **modes** for different tasks 
- Most notable example is **VIM**
	- Neovim
	- Kakoune
	- Evil mode
	- Emacs
	- Helix

# Brief History 
- Vi created by Bill Joy in 1976
- Vim created by Bram Moolenaar in 1991 
- Vim is a superset of Vi, with many additional features
- Vim is open-source 
- NeoVim is popular fork if Vim that aims to improve the extensibility and maintainability of the codebase

Vim can be combined with tiling software like tmux to create a customizable IDE 

# Pros and Cons 
## Pros
- Muscle memory and speed
- Declarative vs. Imperative
	- Declarative: you specify what you want the computer to do
	- Imperative: you tell the computer how to do it
	- A modal editor is closer to a declarative version of text editing
- Automation
- Customization
## Cons
- Learning Curve
- Unintuitive at first
- Context switching

# Modes
The usual modes are :
- Normal modes: for moving around the text
- Insert mode: for typing text
- Visual mode: for selecting text

A non-modal editor uses the keys for insertion, and the mouse, or non-character keys for selection and navigation

A modal editor uses the same keys for all three modes. Then behavior of the keys change depending on the mode 

# Vim Tutor Section
## Navigation
- To move the cursor press the h,j,k,l keys 
	- k is up
	- j is down
	- h is left
	- l is right
- If you are in another mode like say insert mode you can hit ESC to get back into navigation mode or normal mode

## Start Vim
- In your terminal or shell type in the command vim FILENAME             < ENTER > 

## Leaving Vim
- :q1 < Enter >
	- This exists the editor, DISCARDING any changes you have made

## Deletion
- Pressing "x" deletes a character under the cursor
- This takes us into delete mode

## Insertion
- Pressing "i" to insert text
- Pressing "i" takes us into insert mode

## Appending
- Press "A" to append text
- When doing "shift" + "A" it jumps the cursor to the end of the line and we can insert whatever character we want

## Editing A File
- Using the command ":wq" to save a file and exit
