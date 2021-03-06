# Command bar

The command bar is opened by pressing Ctrl-e. It is a single-line buffer,
meaning that all keybindings from a normal buffer are supported (as well
as mouse and selection).

When running a command, you can use extra syntax that micro will expand before
running the command. To use an argument with a space in it, put it in
quotes. The command bar parser uses the same rules for parsing arguments that
`/bin/sh` would use (single quotes, double quotes, escaping). The command bar
does not look up environment variables.

# Commands

Micro provides the following commands that can be executed at the command-bar by
pressing `Ctrl-e` and entering the command. Arguments are placed in single
quotes here but these are not necessary when entering the command in micro.

* `bind 'key' 'action'`: creates a keybinding from key to action. See the
   `keybindings` documentation for more information about binding keys.
   This command will modify `bindings.json` and overwrite any bindings to
   `key` that already exist.

* `help 'topic'?`: opens the corresponding help topic. If no topic is provided
   opens the default help screen.

* `save 'filename'?`: saves the current buffer. If the file is provided it
   will 'save as' the filename.

* `quit`: quits micro.

* `replace 'search' 'value' 'flags'?`: This will replace `search` with `value`. 
   The `flags` are optional. Possible flags are:
   * `-a`: Replace all occurrences at once
   * `-l`: Do a literal search instead of a regex search

   Note that `search` must be a valid regex (unless `-l` is passed). If one 
   of the arguments does not have any spaces in it, you may omit the quotes.

* `replaceall 'search' 'value'`: this will replace all occurrences of `search`
   with `value` without user confirmation.

	See `replace` command for more information.

* `set 'option' 'value'`: sets the option to value. See the `options` help topic for
   a list of options you can set. This will modify your `settings.json` with the
   new value.

* `setlocal 'option' 'value'`: sets the option to value locally (only in the current
   buffer). This will *not* modify `settings.json`.

* `show 'option'`: shows the current value of the given option.

* `run 'sh-command'`: runs the given shell command in the background. The 
   command's output will be displayed in one line when it finishes running.

* `vsplit 'filename'`: opens a vertical split with `filename`. If no filename is
   provided, a vertical split is opened with an empty buffer.

* `hsplit 'filename'`: same as `vsplit` but opens a horizontal split instead of a
   vertical split.

* `tab 'filename'`: opens the given file in a new tab.

* `tabswitch 'tab'`: This command will switch to the specified tab. The `tab` can
   either be a tab number, or a name of a tab.

* `textfilter 'sh-command'`: filters the current selection through a shell command
   as standard input and replaces the selection with the stdout of the shell command.
   For example, to sort a list of numbers, first select them, and then execute
   `> textfilter sort -n`.
					 
* `log`: opens a log of all messages and debug statements.

* `plugin 'list'`: lists all installed plugins.

* `plugin version 'pl'`: shows version for specified plugin.

* `plugin info 'pl'`: shows additional info for specified plugin.

* `reload`: reloads all runtime files.

* `cd 'path'`: Change the working directory to the given `path`.

* `pwd`: Print the current working directory.

* `open 'filename'`: Open a file in the current buffer.

* `reset 'option'`: resets the given option to its default value

* `retab`: Replaces all leading tabs with spaces or leading spaces with tabs
   depending on the value of `tabstospaces`.

* `raw`: micro will open a new tab and show the escape sequence for every event
   it receives from the terminal. This shows you what micro actually sees from
   the terminal and helps you see which bindings aren't possible and why. This
   is most useful for debugging keybindings.

* `showkey`: Show the action(s) bound to a given key. For example
   running `> showkey CtrlC` will display `Copy`.

---

The following commands are provided by the default plugins:

* `lint`: Lint the current file for errors.

* `comment`: automatically comment or uncomment current selection or line.
