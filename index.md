# Git Tutorial

Hopefully you already went through [installing git](installing_git.md). What you will do now is try the tasks in the [challenges](challenges.md) page using the hints from [cheat_sheeet](cheat_sheet.md).

* [installing git](installing_git.md)
* [challenges](challenges.md)
* [cheat_sheeet](cheat_sheet.md)


### Using Vi

Git will normally call the text editor __vi__ when needed. People love __vi__ because it is so powerful, but it is not super beginner friendly.

I think that learning some __vi__ is just good for you (like eating spinach), so you can find a few basic commands below. If you still hate it, you can tell git to use a different text editor by default.

### Vi Quick reference

Firing up __vi__ is easy, just type `vi` in the shell. If you want to sart a new file or open an extisting one, just enter `vi my_file_name.txt`.

The ticky thing about __vi__ is that it has different modes: one for entering commands and another for actually typing text.

* hit `i` to start __insert mode__, i.e. to be able to type text. You should see `--INSERT--` at the bottom of the editor.
* hit `esc` to start __command mode__, i.e. to enter commands, like saving file or quitting __vi__
* When in __command mode__ you can enter these commands followed by `return`:
   * `:w` Save changes to file
   * `:x` Exit and Save changes
   * `:q!` Exit _Without_ saving
