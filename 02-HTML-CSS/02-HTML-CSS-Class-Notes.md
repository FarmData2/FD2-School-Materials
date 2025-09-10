# 02 - HTML-CSS - Class Notes

## Instructor ToDo Before Class

- Merge:
  - `02-HTML-CSS-Tutorials-Soln` branch into `upstream` `development`.
  - `02-HTML-CSS-Application-Starter` branch into `upstream` `development`.

## Synchronizing `development` with the Upstream

- As we move through the course, I will be merging starter code and solutions to assignments to the upstream `development` branch.
  - So you will frequently need to synchronize your `development` branch with the `upstream` to get the solutions and starter code.
    ![Diagram showing the steps in the forking/branching workflow using Git and GitHub.](../GitReference/GitGitHubWorkFlow.png "The forking/branching workflow.")
  - To synchronize your `development` with the `upstream`.
    - Use a Codespace from a fork not from the upstream (like they will be doing).
    - In a terminal in the Codespace
      ```
      git switch development
      git pull --ff-only upstream development
      git push origin development
      ```
    - Show new directory in the FarmData2 repo in VSCodium.
      - `02-HTML-CSS-Tutorials-Soln`
      - For the in class activities you can:
        - Start from the branch you made for the tutorials.
        - Or you can make a new branch from development and use the solution that I posted.
    - Steps for synchronizing are in the [Git/GitHub Reference](../GitReference/GitReference.md).

## Linting and Pre-Commit Hooks

- May have noticed that when you make a commit a bunch of "stuff" happens.
  - Create a 
  - Make a valid change to `index.html`
    - Commit it
    - Pre-commit hook will run
      - It runs _linting_ tools
        - `cSpell` - Spell checker
        - `esLint` - Formatting checker (and fixer)
        - `vale` - Prose linting - Grammar, readability, potentially offensive language.
  - Make a change with a spelling error.
    - Try to commit it.
      - The commit will fail with a message.
      - Fix the issue.
      - Look at `git status`
        - The `index.html` file is both staged and unstaged.
          - Old change with the problem is staged.
          - New change with the fix is not staged.
      - Stage the new changes.
      - Make the commit.
  - Note that VSCodium will show the errors so you don't have to wait for a commit to fix them.
    - Add another spelling error as an example to show error in VSCodium.

## Reading the MDN HTML / CSS Documentation

- Use a browser not in the Codespace so it doesn't time out.

- Show HTML / CSS Resources on MDN
  - Talk through how to use / read them
  - HTML: https://developer.mozilla.org/en-US/docs/Web/HTML
    - Left column: Reference -> Elements  
    - Use "Filter" to find elements
      - `<a>`
        - show `href` attribute that we used.
        - show `target` attribute as example of a new one.
        - show Examples section.
      - `<img>`
        - for `src` and `alt` attributes that we used
        - show `height` and `width` as examples of new ones.
      - `<input>`
        - Highlight idea of different `type`s
        - You'll use this in the homework H02.
  - CSS: https://developer.mozilla.org/en-US/docs/Web/CSS
    - Left Column: CSS Reference -> Selectors-> Type
      - show Examples section.
      - Example sets the `background-color` of a `<span>`.
    - Left Column: Class and ID are also there.
      - As well as some others that we will not use.
    - How to know what properties there are:
      - CSS menu -> Properties
        - "Alphabetical index of properties" on the left.
        - `background-color` that was used is in there.
        - Lots and lots and lots of these.
          - We will only use a few.
    - Some of the properties we use frequently are part of the "Box Model" that was introduced in the tutorial.
      - CSS menu -> Properties -> Box model
        - Content: the HTML element.
        - Padding: space between that element and any border that is set.
        - Margin: space between the border and any adjacent element's margin.
      - CSS properties for setting the size of these areas are listed and described.

## Hands-on Activities
    
- [02-HTML-CSS-Hands-On.md](./02-HTML-CSS-Hands-On.md)

## Homework Introduction

### Setup

- While they are working on the Hands-on:
  - Using a Codespace on the upstream
    - Switch to the `02-HTML-CSS-Application-Starter` branch.
    - `npm run build:school`
    - Confirm "HTML-CSS" is in the "FD2 School" menu.
    - Open the repo in VSCodium.

### The Starter Code

- When you are setup for the homework you will see:
  - An "HTML-CSS" option on the "FD2 School" menu.
  - Show the page in the browser.
    - Just some placeholder text to get going.
  - Show the code in VSCodium.
    - Open the `modules/farm_fd2_school/src/entrypoints/` directory
    - Show the `HTML-CSS` directory
      - Created when we synched with the upstream earlier.
    - Open the `HTML-CSS/App.vue` file.
      - This is a Vue App which we'll learn more about soon. 
      - For now notice the `<template>`, `<script>` and <`style`> sections.
        - `<template>` is like the `<body>` of your `index.html` page.
          - You'll be adding HTML elements here to create the page.
        - `<script>` is where our Vue.js code will go.
          - We'll get to that next week.
        - `<style>` is like your `style.css` file.
          - You'll be creating CSS rules for the page here.

### Making and Seeing Changes

- For the homework you'll be editing the `<template>` and `<style>` sections of the `App.vue` file to create a prototype Harvest feature.
  - You'll make and switch to a feature branch.
    ```
    git branch class-demo
    git switch class-demo
    ```
- When you make changes to an `App.vue` page in FarmData2 you won't see the changes immediately.
  - Make a change to the placeholder text in `App.vue`.
  - Show that there is no change to the page in farmOS/FarmData2.
- You need to rebuild the module to see the changes.
  - In a terminal:
    - `npm run build:school`
  - Then "Shift+reload" to see the changes in the browser.
- Rebuild and "Shift+reload" after each change.
  - If time permits...
    - Can use `npm run watch:school` 
    - It will automatically rebuild anytime you save a change to a file in the module.
 
### The End Result

- Show the final product.
  - Switch to the `03-Vue1-Application-Starter` branch.
  - Rebuild
  - "Shift+reload"
  - Visit "Vue1" tab in the "FD2 School" Menu
    - This is my solution to H02.
  - Note that it looks like something...
    - But it doesn't actually do anything.
    - But it will eventually.

### Use an AI to Help

  - Show using Chat-GPT (or whatever AI you like)
  - Ask for:
    - Give me a generic example of an HTML table with 3 columns.
    - Make the first column contain a group of radio buttons.
    - Remove the text from the radio buttons.
  - Ask it to create or illustrate small parts of the code that you already understand at least conceptually how to do.
    - If you ask it for something to big...
      - It's going to give you something that is very hard to adapt well to the assignment. 
    - If you ask it for something you don't actually know how to do...
      - It's going to give you something you don't understand or cant adapt to the assignment.

### Make Incremental Commits

- Make a commit each time you add a new piece of the page.
  - This demonstrates that you did your own work!
  - PR's without incremental commits do not receive full credit.

## How to Follow the Tutorial Videos

- Vue School Tutorials
  - https://vueschool.io/courses/vuejs-3-fundamentals
    - We'll work through these over the next few weeks.
- Each Tutorial assignment will indicate which videos to watch.
- When completing the Tutorial assignments I suggest:
  - Watch the video through once.
  - Restart the video and watch it through the first code change.
  - Make that change.
  - Continue the video through the demonstration of what the change does.
  - Do that demonstration for yourself with our code.
  - Make a commit to your feature branch.
  - Repeat for the next code change and demonstration.
- Start early
  - Work together
    - Side by side
    - Each doing the work on your own machine.
    - Compare code, help each other get it working.
  - Don't spend hours and hours on a single step. 
    - Stop and message me or come to an office hour.

## Instructor ToDo After Class

- Merge:
  - `02-HTML-CSS-Activity-Soln` branch into `development`.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)