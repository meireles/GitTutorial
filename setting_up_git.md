##1. Setting up git

After installing, you'll have to configure git on your computer. This means telling git information about you and your preferences. You only have to do this once, and you can always check what your current configuration is using `git config --list`

First tell git your name, email and that you'd like colored output.

    git config --global user.name "YOUR_NAME"
    git config --global user.email "YOUR_EMAIL"
    git config --global color.ui true

The `--global` flag is telling git to use that same configuration for all repos.

## Default text editor

Git will normally call the text editor __vi__ when needed. People love __vi__ because it is so powerful, but it is not super beginner friendly.

I think that learning some __vi__ is just good for you (like eating spinach), so you can find a few basic commands below. If you still hate it, you can tell git to use a different text editor by default.

### Using vi
--
Firing up __vi__ is easy, just type `vi` in the shell. If you want to sart a new file or open an extisting one, just enter `vi my_file_name.txt`.

The ticky thing about __vi__ is that it has different modes: one for entering commands and another for actually typing text.

* hit `i` to start __insert mode__, i.e. to be able to type text. You should see `--INSERT--` at the bottom of the editor.
* hit `esc` to start __command mode__, i.e. to enter commands, like saving file or quitting __vi__
* When in __command mode__ you can enter these commands followed by `return`:
   * `:w` Save changes to file
   * `:x` Exit and Save changes
   * `:q!` Exit _Without_ saving


### Changing your default text editor
--
__On linux / mac__

I think that the default system editor on a max / linux is __vi__, which is great bug not beginer friendly. You can change your editor to __nano__ by typing:

    git config --global core.editor "nano -w"

__On windows__

I'd install notepad++ and then

    git config --global core.editor "'c:/program files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"

Note that the path to notepad++ can be different on your machine and that I could only test this on an old Windows7 computer.