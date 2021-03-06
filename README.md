# bash
Bash Script Tutorial

## Basic Commands

1. **Print a string**

    * Print with a new line:

        `echo «content»`
        

1. **Traversing directories**

    * Change directory:

        ```bash
        cd «your directory path»
        ```
        * `«your directory path»` can be absolute or relative path:
            * Relative path: path that is relative to current directory.
                * `.`: current directory
                * `..`: parent directory
            * Absolute path: full path from the root to the directory.
        * Example: change directory of current terminal to `~/Code/bash`

            ```bash
            $ cd ~/Code/bash
            ```

    * Get absolute path of current directory:
        
        ```bash
        pwd
        ```
    
2. **List files and directories**

    * Basic *listing*:
        
        ```bash
        ls 
        ```
        * `-F`: distinguish between file and folder by appending `/` to folder.
        * `-a`: show all hidden files and folders.
        * `-R`: show all files and folders recursively (access every file in every foler).
        * `-l`: show long list.

3. **Handling files**

    * *Create* a file:

        ```bash
        touch «your file name»
        ```
        * Example: create a `hello_bash` text file in the current directory.

            ```bash
            touch hello_bash
            ```

    * Copy a file:

        ```bash
        cp «src file» «dst file»
        cp «src file» «dst folder»
        ```

        * Example:
            * Copy `hello_bash` from `~/Code/bash` to `~/Code/script/` with a new name `hello_script`.
                
                ```bash
                $ cp hello_bash ~/Code/script/hello_script
                ```
            * Copy `hello_bash` from `~/Code/bash` to `~/Code/script/` with the same name.
                ```bash
                $ cp hello_bash ~/Code/script/
                ```

    * *Link* files: Instead of copying files all over the places, we can link to the original file to save storage.
        * **Symbolic link**: a physical file that points to another file.

            ```bash
            ln -s «original file» «symbolic link file»
            ```
            * Symbolic link is a representative of a 'pointer' to a file.
        * **Hard link**: a virtual file that is referencing to the original file.

            ```bash
            ln «original file» «hard link file»
            ```
            * Hard link is a representative of a 'reference' to a file.
            * Hard link can only be created if the `«hard link file»` is on the same physical medium. Otherwise, symbolic link must be used.
    * *Move* files:
        ```bash
        mv «src file» «dst file»
        mv «src file» «dst folder»
        mv «src folder» «dst folder»
        ```
        * To **rename** a file, move it to the same directory with the new name.
        * `-i`: overwrite any existing files that have the same names.
        * Example:
            * Move file `hello_bash` to current directory with a new name `hello_script` (renaming):

                ```bash
                $ mv hello_bash hello_script
                ```
            * Move file `hello_bash` to folder `~/Code/script`:

                ```bash
                $ mv hello_bash ~/Code/script
                ```
            * Move folder `~/Code/bash/` to inside folder `~/Code/script

                ```bash
                $ mv ~/Code/bash/ ~/Code/script
                ```
    
    * *Delete* files:
        ```bash
        rm «file»
        rm «folder»
        ```
        * `-rf`: also delete everything inside `«folder»`.
        * `-i`: safe guard when removing files.
        * Example:
            * Delete file `hello_bash`:
            
                ```bash
                $ rm hello_bash
                ```
            * Delete folder `~/Code/script` and everything inside it:

                ```bash
                $ rm -rf ~/Code/script
                ```

4. **Managing directories**

    * *Create* a new directory:
    
        ```bash
        mkdir «new folder»
        ```
        * `-p`: also create parent directories (if not exist).
        * Example: create a new folder `tutor` inside current directory:

            ```bash
            mkdir tutor
            ```
    * *Delete* a directory:

        ```bash
        rm «folder»
        rmdir «folder»
        ```
        * Example: delete folder `tutor` inside current directory

            ```bash
            rmdir tutor
            ```

5. **View contents**

    * View *file type*:

        ```bash
        file «file»
        file «folder»
        ```
    
    * View the *whole* file:

        * Print the whole content of file to terminal:
            ```bash
            cat «file»
            ```
            * `-n`: line number.
            * `-T`: remove tab appearance.

        * View content of file page by page:
            ```bash
            more «file»
            less «file»
            ```

    * View *part* of the file:
        * View the **head** of the file:

            ```bash
            head «file»
            ```
            * `-n «line-number»`: show the first `«line-number»` lines.

        * View the **tail** of the file:

            ```bash
            tail «file»
            ```
            * `-n «line number»`: show the last `«line number»` lines.

6. **Peek processes.**

    * *Show all* processes belong to current user.

        ```bash
        ps
        ```
        * `-ef`: show all processes on the system.
        * `-l`: long format to show full information.
        * `--forest`: show relationships between parents and children shells.
    * *Stop* a process:

        ```bash
        kill «pid»
        killall «process-regex»
        ```
    
7. **Monitor disk spaces.**

    * *Show all* media disks attached to the computer.

        ```bash
        mount
        ```
    
    * Show available *disk spaces* on device:

        ```bash
        df
        ```
        * `-h`: human-readable format

    * Show *disk usages*:

        ```bash
        du
        ```
        * `-h`: human-readable format

8. **Working with data files.**

    * *Sort* data:

        ```bash
        sort «file»
        ```
        * Sort file line by line using lexicographical order and locality.
        * `-n`: sort by treating each line a number.
        * `-M`: sort by recognizing the first 3 letters as Month.

    * *Search* data:

        ```bash
        grep «options» «regex» «file»
        ```
        * `«options»`: 
            * `-v`: reverse search (anti-pattern).
            * `-n`: show line number.
            * `-c`: count how many matches.
            * `-e «pattern»`: to specify multi patterns, add `-e` before and concatenate them to the command line.
        * `«regex»`: pattern regular expression

    * *Compress* data:

        * `.bz2` extension:

            ```bash
            bzip2 «file or folder»
            ```

        * `.z' extension:

            ```bash
            compress «file or folder»
            ```
        
        * `.zip` extension:

            ```bash
            zip «file or folder»
            ```

        * `.gz' extension:

            ```bash
            gzip «file or folder»
            ```
    
    * *Archive* data: more popular

        ```bash
        tar «function» «options» «object1» «object2» ...
        ```

        * `-A`: **concatenate** one archive to another.
        * `-c`: **create** a new archive.
        * `-r`: **append** files to an archive.
        * `-t`: **list** content of an archive.
        * `-u`: **update** existing files inside the archive with new files.
        * `-x`: **extract** files from the arhive.

9. **Tips on shells**

    * *Multiple* commands in one line: commands are executed directly in the current shell.

        ```bash
        «command-1» ; «command-2» ; «command-3» ; ...
        ```

    * *Process list*: commands are executed in a subshell generated by the current shell.

        ```bash
        ( «command-1» ; «command-2» ; ... )
        ```

    * *Idle* a shell:

        ```bash
        sleep «duration»
        ```

    * *Background* mode: add `&` to the end of a command.

        ```bash
        «command» &
        ```
        * To display background jobs, `jobs` command can be used:

            ```bash
            jobs
            ```
        
    * *Co-processing*: co-processing is the same as background mode but in the subshell.

        ```bash
        coproc «command»
        coproc «job name» { «command-1» ; «command-2» ; ... ; }
        coproc «process list»
        ```
    
    * *History* commands: show history of commands used.

        ```bash
        history
        ```

    * Command *aliases*: create alias name for complex (or long) command.

        ```bash
        alias «alias-command»='«command»'
        ```
        * `-p`: show all aliases.

7. **Variables**

    * View all *environment* (global) variables:

        ```bash
        printenv
        ```

    * View value of a variable *individually*:

        ```bash
        env «variable»
        echo $«variable»
        ```
        * Tips: Use `$` if you only read the variable. Omit `$` if you want to make changes to the variable. (Except for the only case of `env`)

    * View *both* global and local variables:

        ```bash
        set
        ```

    * Set a value to a *local* variable:

        ```bash
        «variable»=«value»
        ```
        * `«value»` can be a number or a string. If it is a string containing spaces, `"` must be used.
        * Local variable can be only available to the current shell, not to child shells (and vice versa).

    * Create a *global* variable: First, we generate a local variable. Then, use command `export` to publish it globally.

        ```bash
        export «local variable»
        export «variable»=«value»
        ```

    * *Remove* a local variable:

        ```bash
        unset «variable»
        ```
    
    * `$PATH` global variable: contains directories for commands and binaries of the system.
        * To **append** another directory to the path (*locally* in the current shell):

            ```bash
            PATH=$PATH:«new directory»
            ```
        
        * To update it to be available *globally* (to be used by child shells):

            ```bash
            export PATH=$PATH:«new directory»
            ```

    * Variable *array*:
        * *Create* an array:

            ```bash
            «variable» = ( «value» «value» ... )
            ```
        
        * *Get* value of an array: (`[]` must not be omitted)

            ```bash
            «variable»[«index»]
            ```
            * `«index»` can be replaced with `*` to get all elements.
            * `unset` can be used to remove an element from array but the array size is not changed. It is only the value at the index is null.

## File Permissions

1. **Linux Security**

    * `/etc/passwd`: this file contains users' basic information and UID.
    * `/etc/shadow`: this file contains users' authentication information (such as password).
    * Add a new user: (will be updated later)

2. **Linux Groups**

    * Grouping allows particular users in a group to share resources.
    * Each group is recognized by its ID, called GID.
    * `/etc/group`: this file contains groups' basic information and GID.
    * Create new group: (will be updated later)

3. **File Permissions**

    * File permissions can be reviewed via output of command `ls -l`.
    * Permission *format*:

        ```bash
        rwx
        ```
        * `r`: read permission
        * `w`: write permission
        * `x`: execute permission
        * `-`: if any of permissions are not permitted, `-` will replace.

    * Format of permissions of an object in file system: (no space between them)

        ```bash
        «type» «owner» «group» «others»
        ```
        * `«type»`: types of files.
            * `-`: files
            * `d`: directories
            * `l`: links
            * `c`: character devices
            * `b`: block devices
            * `n`: network devices
        * `«owner»`, `«group»`, `«others»` are permissions that follow the format of permissions above.
    
    * *Default* file permissions:

        ```bash
        umask
        ```
        * Show the **octal** value of permission above (converted from binary: 0 for `-`, 1 for characters ).
        
            String | Binary | Octal
             --- | --- | --- 
            `---` | 000 | 0
            `--x` | 001 | 1
            `-w-` | 010 | 2
            `-wx` | 011 | 3
            `r--` | 100 | 4
            `r-x` | 101 | 5
            `rw-` | 110 | 6
            `rwx` | 111 | 7

    * *Change* file permission:

        ```bash
        chmod «options» «mode» «file»
        ```
        * `«options»`: can be omitted
            * `-r`: recursively change permissions of children files and folders.
        * `«mode»`: there are 2 ways
            * **Octal** value: combine octal values of `«owner-permission»`, `«group-permission»`, `«others-permission»`.

                ```bash
                # r-xrw-rwx
                chmod 567 «file»
                ```
            * Set **individually** value of 3 types of permission (owner, group and others).

                ```bash
                «Field»«Op»«Value»
                ```
                * `«Field»`: types of permissions
                    * `u`: user
                    * `g`: group
                    * `o`: others
                    * `a`: all of the above
                * `«Op»`: operations
                    * `+`: add permission
                    * `-`: remove permission
                    * `=`: set permission
                * `«Value»`: value of permissions
                    * Can be replaced with the same value as `«Field»` when using `=`. This means that one type of permission can be configured the same as another.
                    * `X`: execute permission iff the directory is also permitted.
                    * `s`: set UID or GID for permission.
                    * `t`: save program text.
        * Change ownership: (will be updated later)

## Basic Shell Scripting

1. **Script file**

    * *Create* a script file: a script file is a text file that is prepended with `#!/bin/bash`

        ```bash
        #!/bin/bash
        ...
        ```
    
    * *Comment*: a line is commentted out by using `#`.

        ```bash
        # This is a comment
        ```
    
    * *Print* a message:

        ```bash
        echo «message»
        ```
        * To **insert** a variable into a message, use `$variable`.

            ```bash
            echo "This is a hello world message, $variable"
            ```
    
    * *Command substitution*: useful for formatting script.
        * Use back-ticks ` ` `.

            ```bash
            hello=`world`
            ```
        
        * Use `$()`:

            ```bash
            hello=$(world)
            ```

        * Command substitution creates a subshell to run those commands. Therefore, there might be some local variables in the current shell that are not available in those shells.

2. **Redirect input and output**

    * Redirect *output*: everything from standard output is redirected to the specified output text file.

        ```bash
        «command» > «output-file»
        ```

    * Redirect *input*: everything from standard input is redirected to the command.

        ```bash
        «command» < «input-file»
        ```
    
    * *Inline* input redirection:

        ```bash
        «command» << «marker» «content» «marker»
        ```
        * «marker» can be any characters (or string).
        * Only `«content»` part will be the standard input of `«command»`.

3. **Pipes**

    ```bash
    «command-1» | «command-2» | ...
    ```
    * Standard output `«command-1»` will be redirected to be standard input of `«command-2»`.


4. **Math operations**

    * `expr` command: (will be updated)
    * Brackets `$[]`:

        ```bash
        variable=$[1 + 2]
        ```

    * All basic operations are integer operations.
    * To resolve *floating point* number, use `bc` package.

        ```bash
        result = $(echo "«options» ; «expression»" | bc)
        ```

5. **Exit script**

    * Exit *status code* from the last command:

        ```bash
        echo $?
        ```
        * **Table** of exit codes:

            Code | Description
            --- | ---
            `0` | Successful execution of command
            `1` | Unknown error
            `2` | Misuse of shell command
            `126` | Cannot execute command
            `127` | Command not found
            `128` | Invalid exit argument
            `128+x` | Fatal error with signature `x`
            `130` | Command terminated with `Ctrl+C`
            `255` | Exit status code out of range

    * Exit command:

        ```bash
        exit «code»
        ```

6. **Structured Commands**

    * `if-then` statement:

        ```bash
        if «command»
        then
            «command-1»
            «command-2»
            ...
        fi
        ```
        * The `«command»` after `if` is not the same as other programming languages.
        * Result of the `«command»` condition is based on its exit code.
            * If the exit code is 0, it means the `«command»` executes successfully and leads to the list of commands inside.
            * Otherwise, it skips the inside.

    * `if-then-else` statement:

        ```bash
        if «command»
        then
            «command-y-1»
            «command-y-2»
            ...
        else
            «command-n-1»
            «command-n-2»
            ...
        fi
        ```
        * The mechanism is the same as `if-then` statement except that it redirects to `«command-n-*»` list to execute.

    * `elif` statement: equivalent to `else if` to other programming languages.

        ```bash
        if «command-1»
        then
            «command-1-1»
            ...
        elif «command-2»
        then
            «command-2-1»
            ...
        elif «command-3»
        then
            «command-3-1»
            ...
        else
            ...
        fi
        ```

    * Comparison: To actually apply comparison, add `[]` to the commands after `if`, `elif`.

        ```bash
        if [ «comparison» ]
        then
            ...
        elif [ «comparison» ]
        then
            ...
        ...
        ```

        * Double square brackets:

        ```bash
        if [[ «comparison» ]]
        then
            ...
        elif [[ «comparison» ]]
        then
            ...
        ...
        ```
            * Square brackets remove the requirements of enclosing numeric literals and variables (in both string and numeric comparison) with double quotes `""`.

        * Numeric comparison:

            Operation | Comparison
            --- | ---
            `n1 -eq n2` | Equal to
            `n1 -ne n2` | Not Equal to
            `n1 -gt n2` | Greater Than
            `n1 -lt n2` | Less Than
            `n1 -ge n2` | Greater than or Equal to
            `n1 -le n2` | Less than or Equal to

            * `n1` and `n2` can be replaced by a variable or an integer number (no floating point number).
            * Examples: Single bracket and Double brackets are the same in this situation

                ```bash
                [ 123 -eq 222 ]
                [ $x -gt 333 ]
                [ 333 -le $x ]
                ```
        
        * String comparison:

            Operation | Comparison
            --- | ---
            `-n str` | Check if `str` has length > 0
            `-z str` | Check if `str` has length = 0
            `str1 = str2` | Check if `str1` less than `str2`
            `str1 != str2` | Check if `str1` less than `str2`
            `str1 < str2` | Check if `str1` less than `str2`
            `str1 > str2` | Check if `str1` greater than `str2`
            * All these comparisons are lexicographical order only and does not take into account of locality.
            * `str`, `str1`, `str2` can be replaced by any variable or string (string format in bash is enclosed by double quotes: `"content"`).
            * Examples:

                Single Bracket | Double Brackets
                :---: | :---:
                `[ "xyz" = "abc" ]` | `[[ "xyz" = "abc" ]]`
                `[ "$v" = "abc"]` | `[[ $v = "abc" ]]`
                `[ "abc" = "$v" ]` | `[[ "abc" = $v ]]`
                `[ $v = $u ]` | `[[ $v = $u ]]`

        * File comparison:

            Operation | Comparison
            --- | ---
            `-d obj` | Check if `obj` is a directory
            `-e obj` | Check if `obj` exists
            `-f obj` | Check if `obj` exists and is a file (not a directory)
            `-r obj` | Check if `obj` is readable
            `-w obj` | Check if `obj` is writable
            `-x obj` | Check if `obj` is executable
            `-s obj` | Check if `obj` is not empty
            `-O obj` | Check if `obj` exists and owned by the current user
            `-G obj` | Check if `obj` exists and belongs to the same group of current user.
            `obj1 -nt obj2` | Check if `obj1` is New Than `obj2`
            `obj1 -ot obj2` | Check if `obj1` is Older than `obj2`
            * `obj`, `obj1` and `obj2` can be replaced by any variable or file/folder name string.
        
    * Compound comparison:

        * Logical OR:

        ```bash
        [ «condition-1» ] || [ «condition-2» ]
        ```

        * Logical AND:

        ```bash
        [ «condition-1» ] && [ «condition-2» ]
        ```

        * Nested comparisons: use double brackets `[[ condition ]]`.

        ```bash
        [[ ... && ... || ... || ]]
        ```

    * Double parentheses: use `(( ))` for advanced mathemtical operations and/or comparison.
        * `++var`: pre-increment
        * `--var`: pre-decrement
        * `var++`: post-increment
        * `var--`: post-decrement
        * `!`: logical negation
        * `~`: bitwise negation
        * `**`: exponentiation
        * `<<`: bitwise left shift
        * `>>`: bitwise right shift
        * `&`: bitwise AND operator
        * `|`: bitwise OR operator
        * `&&`: logical AND operator
        * `||`: logical OR operator
    
    * Double Parentheses vs Double Brackets? Use parenthesis for number manipulation and brackets for string handling.

    * Double parentheses can replace conditions inside `if` command.

    * Loops: `for` command

        ```bash
        for «var» in «list»
        do
            « commands »
        done
        ```

        * Example:
            * Read from a string literal:

                ```bash
                for country in Russia England France
                do
                    echo A European country is $country
                done
                ```
            
            * Read from a string variable:

                ```bash
                countries="Russia England France"
                for country in $countries
                do
                    echo A European country is $country
                done
                ```
            
            * Read from a complex string literal:

                ```bash
                for city in "New York" Vancouver "Washinton DC"
                do
                    echo "A USA city is $city"
                done
                ```
            
            * Read values from a command: string returned from command is processed as above.

                ```bash
                for data in $(cat $file)
                do
                    echo data
                done
                ```
            
            * Reading a directory using wildcards:

                ```bash
                for file in ~/bash/*
                do
                    ...
                done
                ```
        
        * C-style loop:

            ```bash
            for (( «var ass»; «condition»; «iteration»))
            do
                ...
            done
            ```
        
            * Example:

                ```bash
                for (( i=0, j=10; i < 10; ++i, j*= 2))
                do
                    echo $i is $j
                done
                ```
            