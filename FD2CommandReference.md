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

Shortcut        | Action
----------------|------------------------------------
`Ctrl-C`        | Copy 
`Ctrl-V`        | Paste
`Ctrl-S`        | Save
`Shift-Ctrl-I`  | Auto format text/code in VSCodium

