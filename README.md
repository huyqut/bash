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

