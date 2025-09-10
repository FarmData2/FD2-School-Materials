# FarmData2 Key Commands and Shortcuts

## Commands

### Building a FarmData2 Module

When changes are made to code in one of the FarmData2 modules it must be rebuilt in order to see the changes in the running farmOS instance.  To rebuild the `fd2_school` module use the command:
```
npm run build:school
```

If you do not see the expected changes after rebuilding a module, reload the page containing the changed code in the browser while holding the "Shift" key. This will discard the cached version of the page and load the new page.

The other modules that can be rebuilt are `fd2` and `examples`.

### Watching a FarmData2 Module

When you are working on a module you can use the `build` command above after each change, or you can run a _watcher_.  A watcher monitors the files in the module for changes and automatically rebuilds the module when any file changes.  To start a watcher on the `school` module use the command:
```
npm run watch:school
```

## Keyboard Shortcuts

A short guide to some essential Keyboard Shortcuts that can be used in the FarmData2 Development Environment.

### Linux Terminal

Shortcut        | Action
----------------|------------------------------------
`Shift-Ctrl-C`  | Copy
`Shift-Ctrl-V`  | Paste
`Ctrl-C`        | Terminate the running program in terminal

### Browser / VSCodium / Etc.

Shortcut             | Action
---------------------|------------------------------------
`Ctrl-C`             | Copy 
`Ctrl-V`             | Paste
`Ctrl-S`             | Save
`Ctrl-Shift-I`       | Auto format text/code in VSCodium
`Ctrl-Shift-I`       | Open the Developer Tools in Firefox
`Alt-z` or `Cmd-z`   | Toggle word wrap in VSCodium

## Linux Terminal Commands

Command              | Action
---------------------|------------------------------------
`ls`                 | List current directory contents
`cd <dir>`           | Change into `<dir>`
`mkdir <dir>`        | Create new directory `<dir>` in the current directory
`rm <file>`          | Delete file `<file>`
`rmdir <dir>`        | Delete directory `<dir>` - must be empty

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)