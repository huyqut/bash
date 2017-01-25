# bash
Bash Script Tutorial

## Basics

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

    * Multiple commands in one line: commands are executed directly in the current shell.

        ```bash
        [command-1] ; [command-2] ; [command-3] ; ...
        ```

    * Process list: commands are executed in a subshell generated by the current shell.

        ```bash
        ( [command-1] ; [command-2] ; ... )
        ```

    * Idle a shell:

        ```bash
        sleep [duration]
        ```

    * Background mode: add `&` to the end of a command.

        ```bash
        [command] &
        ```
        * To display background jobs, `jobs` command can be used:

            ```bash
            jobs
            ```
        
    * Co-processing: co-processing is the same as background mode but in the subshell.

        ```bash
        coproc [command]
        coproc [job-name] { [command-1] ; [command-2] ; ... ; }
        coproc (process-list)
        ```
    
    * History commands: show history of commands used.

        ```bash
        history
        ```

    * Command aliases: create alias name for complex (or long) command.

        ```bash
        alias [alias-command]='[command]'
        ```
        * `-p`: show all aliases.
