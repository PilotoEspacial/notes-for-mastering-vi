# Notas para manejar como un pro el editor de texto VI y sus predecesores, vim, neovim, lvim...


## Lesson 1 SUMMARY

 1. The cursor is moved using either the arrow keys or the hjkl keys.
     h (left)   j (down)       k (up)       l (right)

 2. To start Neovim from the shell prompt type:
~~~ sh
    $ nvim FILENAME
~~~
 3. To exit Neovim type: `<Esc>`{normal} `:q!`{vim} `<Enter>`{normal} to trash all changes.
                OR type: `<Esc>`{normal} `:wq`{vim} `<Enter>`{normal} to save the changes.

 4. To delete the character at the cursor type: `x`{normal}

 5. To insert or append text type:
    `i`{normal} insert text `<Esc>`{normal}     insert before the cursor.
    `A`{normal} append text `<Esc>`{normal}     append after the line.

NOTE: Pressing `<Esc>`{normal} will place you in Normal mode or will cancel
      an unwanted and partially completed command.


## Lesson 2 SUMMARY

 1. To delete from the cursor up to the next word type:    `dw`{normal}

 2. To delete from the cursor to the end of a line type:   `d$`{normal}

 3. To delete a whole line type:                           `dd`{normal}

 4. To repeat a motion prepend it with a number:           `2w`{normal}

 5. The format for a change command is:

        operator   [number]   motion

    where:

        operator -   is what to do, such as [d](d) for delete
        [number] -   is an optional count to repeat the motion
        motion   -   moves over the text to operate on, such as:
                        [w](w) (word),
                        [$]($) (to the end of line), etc.

 6. To move to the start of the line use a zero: [0](0)

 7. To undo previous actions, type:            `u`{normal}  (lowercase u)
    To undo all the changes on a line, type:   `U`{normal}  (capital U)
    To undo the undo's, type:                  `<C-r>`{normal}


## Lesson 3 SUMMARY

 1. To put back text that has just been deleted, type [p](p). This puts the
    deleted text AFTER the cursor (if a line was deleted it will go on the
    line below the cursor).

 2. To replace the character under the cursor, type [r](r) and then the
    character you want to have there.

 3. The [change operator](c) allows you to change from the cursor to where
    the motion takes you. Type `ce`{normal} to change from the cursor to the
    end of the word, `c$`{normal} to change to the end of a line, etc.

 4. The format for change is:

        c   [number]   motion

 ## Lesson 4 SUMMARY

 1. `<C-g>`{normal}     displays your location and the file status.
    `G`{normal}         moves to the end of the file.
    number `G`{normal} moves to that line number.
    `gg`{normal}        moves to the first line.

 2. Typing `/`{normal} followed by a phrase searches FORWARD for the phrase.
    Typing `?`{normal} followed by a phrase searches BACKWARD for the phrase.
    After a search type `n`{normal} to find the next occurrence in the same
    direction or `N`{normal} to search in the opposite direction.
    `<C-o>`{normal} takes you back to older positions, `<C-i>`{normal} to
    newer positions.

 3. Typing `%`{normal} while the cursor is on a (,),[,],{, or } goes to its
    match.

 4. To substitute new for the first old in a line type
~~~ cmd
        :s/old/new
~~~
    To substitute new for all 'old's on a line type
~~~ cmd
        :s/old/new/g
~~~
    To substitute phrases between two line #'s type
~~~ cmd
        :#,#s/old/new/g
~~~
    To substitute all occurrences in the file type
~~~ cmd
        :%s/old/new/g
~~~
    To ask for confirmation each time add 'c'
~~~ cmd
        :%s/old/new/gc
