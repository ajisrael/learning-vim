# Learning Vim

From Primeagen FEM course found [here](https://github.com/ThePrimeagen/vim-fundamentals?tab=readme-ov-file)

## Cleaning Environment

```bash
git clone https://github.com/ThePrimeagen/vim-nav-playground.git
```

## Modes

Normal - motions
Insert - editing text
Visual - highlight text
Visual Line - highlighting text but in lines
Command Mode - executing commands

## Terms

### Files

### Buffers

A buffer contains a representation of the file in memory. The file does not change until you write the buffer to the file.

```bash
:h buffer
```

Help menu for info related to topic, in this case buffer

### Windows

Something that displays a buffer. You can close a window, and the buffer cna remain inmemory.

### Tabs

Another viewport into vim. Separate workspace - ish

### Splits

Splitting a window

### Help Menu

You can open a help menu for pretty much anything with `h: <term>`

### Motion

A command that moves the cursor (from help docs `h: motion`)

### Abbreviations

`Ctrl+a` is abbreviated `<C-a>`. How things are referenced in VimL, Vim's editor language.

Enter is `<CR>` (carrage return)

Tab `<tab>`, Escape `<esc>`, and Space `<space>`

When you see a `:` this will mean it is executing a commmand

## Exercises

Navigation

```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/exercise-0-hjkl-x.md > exercise.md && vim exercise.md
```

Yanking, Deleting, and Register

```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/exercise-1-dyp.md > exercise.md && vim exercise.md
```

Insert

```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/exercise-2-insert.md > exercise.md && vim exercise.md
```

Setting up Views and Integrating Motions

```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/some-javascript.md > exercise.js && vim exercise.js
```

Search and Replace

```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/exercise-3-search-and-replace.md > exercise.md && vim exercise.md
```

Macros

```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/exercise-4-macros.md > exercise.md && vim exercise.md 
```

Registers

```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/exercise-5-registers.md > exercise.md && vim exercise.md
```

## Helpful Commands

### General

#### List available options for a command

```bash
<C-d>
```

Example: Pressing `<C-d>` after `:colorscheme` will give you a list of all availble color schemes to select from

#### Center screen

```bash
zz
```

#### Remove highlights

```bash
:nohls
```

#### View registers

```bash
:reg
```

#### Source current file in vim

```bash
:so %
```

`:so` is the source commmand

`%` is current file

So you could do this with other files too

#### Go to first non whitespace character of line

```bash
_
```

### Explore

#### Open Explore view

```bash
:Ex
```

#### Open Explore view to the side

```bash
:Vex
```

#### Horizontal (Split) explore view

```bash
:Sex
```

### Window Mode

#### Enter Window Mode

```bash
<C-w>
```

Then you can use hjkl for navigation

And s and v for horizontal and vertical split

### Edit

```bash
:e <path-to-file-to-edit>
```

Slow, so you will want a fuzzy finder

### Marks

Bookmarking a file

Navigate to a position in a file. Then press `m` in normal mode followed by a letter for your mark.

Global marks are denoted by a capital letter and are accessable accross buffers.
Local marks are denoted by a lowercase letter and are contained to a buffer

Create new global mark:

```bash
m<capital-letter>
```

Create new local mark:

```bash
m<capital-letter>
```

Jump to mark:
```bash
'<capital-letter>
```

### Alternate File 

You can see your current file and previous file in your registers

```bash
:reg
```

Will output something like this at the bottom:

```bash
  c  "%   src/also-this.c # current file
  c  "#   src/twitch.c    # previous file
```

You can jump to the previous file with either of the following:

```bash
<C-6>
<C-^>
```

### Jumplist

View your jumps

```bash
:jumps
```

Go to previous jump

```bash
<C-o>
```

Go to next jump

```bash
<C-i>
```

### Search & Replace

#### Basic Search

```bash
/<search-string>
```

`n` walks forwards through matches
`N` walks backwards through matches

For highlighting run `:set hls` and to ignore case `:set ic` or just set both in one command

```bash
:set hls ic
```

#### Regex Search

Essentially the same as a basic search just with a regex

```bash
/<search-regex>
```

#### Replace

You can use the same syntax as for search as for a find and replace in terms of the selected range.

```bash
%     # entire file
1,4   # lines 1 through 4
'<,'> # selected range (auto populates if : is pressed in visual mode)
      # no range will just apply to current line
```

Format is:

```bash
:<range>s/<search-token>/<replacement-token>
```

You can also add a `g` to the end to replace all instances as it will only replace the first instance on a line by default
You can also add a `c` to the end to ask for confirmation for each instance of the replace you're about to do

Getting fancy with search tokens:

Lets say you have the following if statements and you wanted to swap the first condition with the second condition it is anded with.

```bash
if (foo && bar) {
} else if (bar && baz) {
} else if (baz && foo) {
} 
```

You can select that range and execute the following command:

```bash
:'<,'>s/(\(.*\) && \(.*\))/(\2 \&\& \1)
```

The `\(.*\)` (AKA, fighting one-eyed kirby) is telling the regex expression to save that selected region to a variable.
That variable corresponds to a number starting at 1 for each instance of the one-eyed kirby.

We also need to escape the `&` because they execute a command

```bash
if (bar && foo) {
} else if (baz && bar) {
} else if (foo && baz) {
} 
```

### Macros

Allows you to record and replay keystrokes. (Also creates Macro Pressure anytime you try and record anything)
Begin recording by pressing `q` in normal mode. Then press the character you want to bind to. (Typically people use `a`). This will start a recording session for the macro you are about to create.
Now enter in your keystrokes and finish your recording with q. It will only stop recording if q is pressed in normal mode.
To play your macro press `@` and the character you bound the macro to. You can combine this with numbers just like any motion.
For example if you bound your macro to `a` then `100@a` would play that macro 100 times.

Your macros will be stored in a register corresponding to the character you bound.

### Registers

As simple as a key value store. Keys are characters and values are strings.

You view registers with the `:reg` command.

You can yank into a register as well. All registers start with the `"` character.

```bash
V"by
```

This will yank the contents of the current line into register `b` (`"b`)

Likewise you can also paste the contents of a register:

```bash
"bp
```

This will paste the contents of register `b`

This means you can edit macros. You can also play the contents of a register as a macro with `@` then the register value. Example with register `b` would be `@b`

## Notes

Not recommended for Java

Remaps will cause there to be a pause on the first key as you execute a remap. So make sure they start with something you don't use often or conflict with another command.
