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

## Notes

Not recommended for Java

Remaps will cause there to be a pause on the first key as you execute a remap. So make sure they start with something you don't use often or conflict with another command.
