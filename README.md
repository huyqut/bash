# bash
Bash Script Tutorial

## Basics

1. Traversing directories

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
    
2. List files and directories

    * Basic listing:
        
        ```bash
        ls 
        ```
        * `-F`: distinguish between file and folder by appending `/` to folder.
        * `-a`: show all hidden files and folders.
        * `-R`: show all files and folders recursively (access every file in every foler).
        * `-l`: show long list.

3. Handling files

    * Create a file:

        ```bash
        touch [file-name]
        ```

    * Copy a file:

        ```bash
        cp [from-file] [to-file]
        cp [from-file] [to-folder]
        ```

    * Link files: Instead of copying files all over the places, we can link to the original file to save storage.
        * Symbolic link: a physical file that points to another file.

            ```bash
            ln -s [original-file] [symbolic-link-file]
            ```
            * Symbolic link is a representative of a 'pointer' to a file.
        * Hard link: a virtual file that is referencing to the original file.

            ```bash
            ln [original-file] [hard-link-file]
            ```
            * Hard link is a representative of a 'reference' to a file.
            * Hard link can only be created if the `[hard-link-file]` is on the same physical medium. Otherwise, symbolic link must be used.
    * Move files:
        ```bash
        mv [from-file] [to-file]
        mv [from-file] [to-folder]
        mv [from-folder] [to-folder]
        ```
        * To rename a file, move it to the same directory with the new name.
        * `-i`: overwrite any existing files that have the same names.
    
    * Delete files:
        ```bash
        rm [file]
        rm [folder]
        ```
        * `-rf`: also delete everything inside `[folder]`.
        * `-i`: safe guard when removing files.
4. Managing directories

    * Create a new directory:
    
        ```bash
        mkdir [new-folder]
        ```
        * `-p`: also create parent directories (if not exist).
    * Delete a directory:

        ```bash
        rm [folder]
        rmdir [folder]
        ```

5. View contents

    * View file type:

        ```bash
        file [file]
        file [folder]
        ```
    
    * View the whole file:

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

    * View part of the file:
        * View the head of the file:

            ```bash
            head [file]
            ```
            * `-n [line-number]`: show the first `[line-number]` lines.

        * View the tail of the file:

            ```bash
            tail [file]
            ```
            * `-n [line-number]`: show the last `[line-number]` lines.
    