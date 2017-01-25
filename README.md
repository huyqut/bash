# bash
Bash Script Tutorial

## Basic Commands

1. **Traversing directories**

    * Change directory:

        ```bash
        cd /your/directory/path
        ```
        * `/your/directory/path` can be absolute or relative path:
            * Relative path: path that is relative to current directory.
                * `.`: current directory
                * `..`: parent directory
            * Absolute path: full path from the root to the directory.

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
        touch [file-name]
        ```

    * Copy a file:

        ```bash
        cp [from-file] [to-file]
        cp [from-file] [to-folder]
        ```

    * *Link* files: Instead of copying files all over the places, we can link to the original file to save storage.
        * **Symbolic link**: a physical file that points to another file.

            ```bash
            ln -s [original-file] [symbolic-link-file]
            ```
            * Symbolic link is a representative of a 'pointer' to a file.
        * **Hard link**: a virtual file that is referencing to the original file.

            ```bash
            ln [original-file] [hard-link-file]
            ```
            * Hard link is a representative of a 'reference' to a file.
            * Hard link can only be created if the `[hard-link-file]` is on the same physical medium. Otherwise, symbolic link must be used.
    * *Move* files:
        ```bash
        mv [from-file] [to-file]
        mv [from-file] [to-folder]
        mv [from-folder] [to-folder]
        ```
        * To **rename** a file, move it to the same directory with the new name.
        * `-i`: overwrite any existing files that have the same names.
    
    * *Delete* files:
        ```bash
        rm [file]
        rm [folder]
        ```
        * `-rf`: also delete everything inside `[folder]`.
        * `-i`: safe guard when removing files.
4. **Managing directories**

    * *Create* a new directory:
    
        ```bash
        mkdir [new-folder]
        ```
        * `-p`: also create parent directories (if not exist).
    * *Delete* a directory:

        ```bash
        rm [folder]
        rmdir [folder]
        ```

5. **View contents**

    * View *file type*:

        ```bash
        file [file]
        file [folder]
        ```
    
    * View the *whole* file:

        * Print the whole content of file to terminal:
            ```bash
            cat [file]
            ```
            * `-n`: line number.
            * `-T`: remove tab appearance.

        * View content of file page by page:
            ```bash
            more [file]
            less [file]
            ```

    * View *part* of the file:
        * View the **head** of the file:

            ```bash
            head [file]
            ```
            * `-n [line-number]`: show the first `[line-number]` lines.

        * View the **tail** of the file:

            ```bash
            tail [file]
            ```
            * `-n [line-number]`: show the last `[line-number]` lines.

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
        kill [pid]
        killall [process-regex]
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
        sort [file-name]
        ```
        * Sort file line by line using lexicographical order.
        * `-n`: sort by treating each line a number.
        * `-M`: sort by recognizing the first 3 letters as Month.

    * *Search* data:

        ```bash
        grep [options] [pattern-regex] [file]
        ```
        * [options]: 
            * `-v`: reverse search (anti-pattern).
            * `-n`: show line number.
            * `-c`: count how many matches.
            * `-e [pattern]`: to specify multi patterns, add `-e` before and concatenate them to the command line.
        * [pattern-regex]: pattern regular expression

    * *Compress* data:

        * `.bz2` extension:

            ```bash
            bzip2 [file-folder]
            ```

        * `.z' extension:

            ```bash
            compress [file-folder]
            ```
        
        * `.zip` extension:

            ```bash
            zip [file-folder]
            ```

        * `.gz' extension:

            ```bash
            gzip [file-folder]
            ```
    
    * *Archive* data: more popular

        ```bash
        tar [function] [options] object1 object2 ...
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
        [command-1] ; [command-2] ; [command-3] ; ...
        ```

    * *Process list*: commands are executed in a subshell generated by the current shell.

        ```bash
        ( [command-1] ; [command-2] ; ... )
        ```

    * *Idle* a shell:

        ```bash
        sleep [duration]
        ```

    * *Background* mode: add `&` to the end of a command.

        ```bash
        [command] &
        ```
        * To display background jobs, `jobs` command can be used:

            ```bash
            jobs
            ```
        
    * *Co-processing*: co-processing is the same as background mode but in the subshell.

        ```bash
        coproc [command]
        coproc [job-name] { [command-1] ; [command-2] ; ... ; }
        coproc (process-list)
        ```
    
    * *History* commands: show history of commands used.

        ```bash
        history
        ```

    * Command *aliases*: create alias name for complex (or long) command.

        ```bash
        alias [alias-command]='[command]'
        ```
        * `-p`: show all aliases.

7. **Variables**

    * View all *environment* (global) variables:

        ```bash
        printenv
        ```

    * View value of a variable *individually*:

        ```bash
        env [variable]
        echo $[variable]
        ```
        * Tips: Use `$` if you only read the variable. Omit `$` if you want to make changes to the variable. (Except for the only case of `env`)

    * View *both* global and local variables:

        ```bash
        set
        ```

    * Set a value to a *local* variable:

        ```bash
        [variable]=[value]
        ```
        * `[value]` can be a number or a string. If it is a string containing spaces, `"` must be used.
        * Local variable can be only available to the current shell, not to child shells (and vice versa).

    * Create a *global* variable: First, we generate a local variable. Then, use command `export` to publish it globally.

        ```bash
        export [local-variable]
        export [variable]=[value]
        ```

    * *Remove* a local variable:

        ```bash
        unset [variable]
        ```
    
    * `$PATH` global variable: contains directories for commands and binaries of the system.
        * To **append** another directory to the path (*locally* in the current shell):

            ```bash
            PATH=$PATH:[new-directory]
            ```
        
        * To update it to be available *globally* (to be used by child shells):

            ```bash
            export PART=$PATH:[new-directory]
            ```

    * Variable *array*:
        * *Create* an array:

            ```bash
            [variable] = ( value0 value1 ... )
            ```
        
        * *Get* value of an array: (`[]` must not be omitted)

            ```bash
            variable[index]
            ```
            * `index` can be replaced with `*` to get all elements.
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

    * Format of permissions of an object in file system:

        ```bash
        [type][owner-permission][group-permission][others-permission]
        ```
        * `[type]`: types of files.
            * `-`: files
            * `d`: directories
            * `l`: links
            * `c`: character devices
            * `b`: block devices
            * `n`: network devices
        * `[owner-permission]`, `[group-permission]`, `[others-permission]` follow the format of permissions above.
    
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
        chmod [options] [mode] [file]
        ```
        * `[options]`: can be omitted
            * `-r`: recursively change permissions of children files and folders.
        * `[mode]`: there are 2 ways
            * **Octal** value: combine octal values of `[owner-permission]`, `[group-permission]`, `[others-permission]`.

                ```bash
                # r-xrw-rwx
                chmod 567 [file]
                ```
            * Set **individually** value of 3 types of permission (owner, group and others).

                ```bash
                [Field][Op][Value]
                ```
                * `[Field]`: types of permissions
                    * `u`: user
                    * `g`: group
                    * `o`: others
                    * `a`: all of the above
                * `[Op]`: operations
                    * `+`: add permission
                    * `-`: remove permission
                    * `=`: set permission
                * `[Value]`: value of permissions
                    * Can be replaced with the same value as `[Field]` when using `=`. This means that one type of permission can be configured the same as another.
                    * `X`: execute permission iff the directory is also permitted.
                    * `s`: set UID or GID for permission.
                    * `t`: save program text.
        * Change ownership: (will be updated later)

## Basic Shell Scripting

1. **Script** file

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
        echo [message]
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
        [command] > [output-file]
        ```

    * Redirect *input*: everything from standard input is redirected to the command.

        ```bash
        [command] < [input-file]
        ```
    
    * *Inline* input redirection:

        ```bash
        [command] << [marker] ... [marker]
        ```
        * [marker] can be any characters (or string).
        * Only `...` part will be the standard input of `[command]`.

3. **Pipes**

    ```bash
    [command-1] | [command-2] | ...
    ```
    * Standard output `[command-1]` will be redirected to be standard input of `[command-2]`.


4. **Math operations**

    * `expr` command: (will be updated)
    * Brackets `$[]`:

        ```bash
        variable=$[1 + 2]
        ```
    * All basic operations are integer operations.
    * To resolve *floating point* number, use `bc` package.
        
        ```bash
        result = $(echo "[options] ; [expression]" | bc)
        ```

5. Exit script

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
        exit [code]
        ```
