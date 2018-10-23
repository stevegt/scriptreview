# scriptreview

A simple tool for browsing `script(1)` output (typescript files).  Using this tool, you can:

- step through a typescript file one command at a time, either forward or backwards
- fast-forward to end of file, or rewind to beginning
- search through the typescript file for a particular string

## background 

Because the `script` command records everything on the tty, including control characters, using `less` to display a `script` output file (typescript) means all of the vt100 control characters for colors, backspaces, etc. get interleaved with the things you actually want to see.  Just stripping those out using `strings` doesn't work either, because the control characters have meaning in a lot of output, as well as in input where you edit a command line before hitting <enter>.  There are tools like `scriptreplay` that do almost the right thing, but they are intended more for continuous replay of a typescript file, e.g. as a screencast, rather than browsing through one command at a time for documentation or review purposes.
   
## status

I threw this together quickly in support of another project.  It works, though it probably still has some bugs and could use some refactoring to make usage more intuitive.  

Right now we just dump all of the results of a command to the screen in one write, which means that `vi` sessions only show the command but no edit session, and long output scrolls off instantly.  We could use some of the features of e.g. https://github.com/scoopex/scriptreplay_ng, to allow speed control of long or complex output.

## install

I really should package this for `pip`.  In the meantime, it's just a single file -- copy or link it into your PATH.
