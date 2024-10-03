# Linux terminal

## Command Line

The shell is a program that interprets your commands and interacts with the operating system.

For now, we will use the bash shell program. See the standard format:

```sh
username@hostname:current_directory
```
The _echo_ command prints the text arguments for display.

```sh
echo Hello World
```

### pwd (Print Working Directory)

Displays the current directory you are in.

```sh
pwd
```

### cd (Change Directory)

Change to another directory using absolute or relative paths.

```sh
$ cd /home/pete/Pictures
```

You can access a given directory by following the example:

```sh
$ cd Hawaii
```

Shortcuts:

- cd . (current directory)
- cd .. (parent directory)
- cd ~ (home directory)
- cd - (previous directory)

### ls (List Directories)

Lists files and directories. Use flags for more options:

- -a (show hidden files)
- -l (long format listing)

```
$ ls -la
```

### touch 

Creates an empty file or updates the timestamp of existing files.

```
$ touch newfile.txt
```

### file

Determines the type of a file.

```
$ file banana.jpg
```

### cat 

Displays the contents of a file or combines multiple files.

```
cat dogfile birdfile
```

It’s not ideal for viewing large files and is meant for short content.

### less

View file content in a paginated manner.

```
$ less document.txt
```

Use the following commands to navigate in less:

- q - Used to quit out of less and return to your shell.
- Page up, Page down, Up and Down - Navigate using the arrow keys and page keys.
- g - Moves to the beginning of the text file.
- G - Moves to the end of the text file.
- /search - You can search for specific text inside the text document by preceding the words you want to search with /.
- h - If you need help on how to use less while you’re in it, use help.

### history

Shows the list of previously entered commands.

```
$ history   
```

### cp (Copy)

Copies files or directories. Use flags to control behavior:

- -r (recursive copy)
- -i (prompt before overwriting)

```
$ cp file1.txt /path/to/destination
```

### mv (Move)

Used for moving files and also renaming them. It is different from the cp command, as mv moves or renames, while cp copies.

You can rename files like this:

```
$ mv oldfile newfile
```

Or you can move a file to a different directory:

```
$ mv file2 /home/pete/Documents
```

And move more than one file:

```
$ mv file_1 file_2 /somedirectory
```

You can also rename directories:

```
$ mv directory1 directory2
```
Flags:

- -i (prompt before overwriting)
- -b (backup the original file  )

### mkdir (Make Directory)

Creates new directories. Use -p to create parent directories

```
$ mkdir newdir
```

### rm (Remove)

Deletes files or directories permanently. Use with caution.

```
$ rm file.txt
```