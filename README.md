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

## Helpful Commands

Center screen

```bash
zz
```

Remove highlights

```bash
:nohls
```

View registers

```bash
:reg
```

## Notes

Not recommended for Java
