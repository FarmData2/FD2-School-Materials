# 03 - Vue1 - Class Notes

## Instructor ToDo Before Class

- Merge 
  - `03-Vue1-Tutorial-Soln`
  - `03-Vue-Activity-Soln`
  - `03-Vue1-Application-Starter`

## Synchronize with `upstream` `development`

- Open dev environment (from a fork as a student)
- `cd FarmData2`
- Synch with `upstream.
  - `git switch development`
  - `git pull upstream development`

## Review 02-HTML-CSS-Application

- Application for today was to build a static HTML prototype for the harvest feature.
  - Show two directories in VSCode:
    - `modules/farm_fd2_school/src/entrypoints/HTML-CSS/App.vue`
      - What you were given to start 02-HTML-CSS-Application.
    - `modules/farm_fd2-school/src/entrypoints/Vue1/App.vue`
      - My solution to 02-HTML-CSS-Application
      - Where you will start 03-Vue1-Application
  - Build the school module: `npm run build:school`
    - Visit FD2 School -> HTML-CSS
      - This was the starter code you were given for the Homework.
    - Visit FD2 School -> Vue1
      - This is my solution to 02-HTML-CSS-Application.
      - It is also the code you are being given to start 03-Vue1-Application.
        ![Static HTML Harvest Prototype](../02-HTML-CSS/images/harvestPrototype.png)
  - The solution:
    - Show the Vue1 page side by side with the code.
    - Filled in the HTML in the `<template>` to create the elements.
    - Added CSS rules to `<style>` to format the page.
      - Date:
        - `value` sets the date. Note ordering `yyyy-mm-dd`
        - `id` all html elements should have an id.
          - Good habit to get into.
          - Allows them to be targeted by CSS id selectors.
            - See: `<style>` for `#harvest-date`
              - Adds 10 pixel margin below to create space between Date and Crop.
      - Crop: 
        - `<label>` and `<select>` with `<option>`s for each choice.
        - The `selected` attribute marks the option as the default option.
        - Styling: 
          - `class="label-margin"` applies the `.label-margin` style.
            - See: `<style>` for `.label-margin`
              - Adds 10 pixels of space between "Date:" and the input.
      - Questions?
        - Other parts of the page you'd like me to show?
        - Questions you had about any of the other elements?
    - 03-Vue1-Application will ask you to apply the content from the 03-Vue1-Tutorials to this page.

## Review 03-Vue1-Tutorial-Soln

- Solution is in `modules/farm_fd2_school/03-Vue1-Tutorials-Soln`
  - `index.html` - where you write the code.
    - Given the code that they start with at the beginning of the video.
  - `main.css` - a provided CSS style sheet.
  - load it from: `file:///home/fd2dev/FarmData2/modules/farm_fd2_school/03-Vue1-Tutorials-Soln/index.html`
- Main points:
  - `<script src="https://unpkg.com/vue@3"></script>`
    - Loads the Vue library.
      - Like an `import` (Java/Python) or `include` (C/C++).
  - `<script>` 
    - Contains a "Vue App"
    - `data()` returns an object that contains the information used by the Vue App.
      - E.g. `header`, `items`
      - Values in the `data` can be included in the page using "Vue's Data Binding".
        - `header`
          - Bound into the `<h1>` using the double moustache `{{ }}`
            - Ignore the `|| 'Welcome'` for now.
          - Causes the value of `header` to appear in the page.
          - Change the `header` it changes the page.
          - The `header || 'Welcome'` is a Javascript shorthand for:
            - If `header` has a non-empty value, show it, otherwise show `'Welcome`'
              - Demo by making `header` an empty string.
              - Then reset it to "Shopping List App".
        - `items`
          - An array of objects in Javascript.
            - `[ ... ]` indicates an array.
              - Array entries are separated by `,`
            - `{ ... }` indicates an object.
              - Each property (i.e. attribute or field) in the object has a name and a value separated by a `:`.
                - `name: value`
                - e.g. `id: 1`, `label: '20 cups'`
              - Object properties are separated by `,`
          - So `items` is an array of three objects, and each object has two properties `id` with a numeric value and `label` with a string value.
            - Note: There is nothing special about `id` it is just the name of a property.  Could have called it anything, `id` just makes semantic sense.
          - Bound into the page using "Vue's List Rendering"
            - In the `<ul>` we generate one `<li>` for each element of `items`:
              - `<li v-for="item in items" ...>`
              - Then use `{{ item.label }}` as the content of the `<li>` to to render the value of the `label` property in the list.
          - The `v-bind:key=item.id` is some stuff for Vue
            - `v-for` needs a unique identifier (i.e. a `key`) for each element.
            - Here `v-bind:key=item.id` tells Vue to use the value of the `id` property as the key because every `item` has a unique `id`.
            - Could also have used `item.label` because they are are all unique as well.  But `item.id` makes more sense semantically.
    - Vue DevTools
      - Open from "Hamburger Menu" -> "More tools" -> "Web Developer Tools"
        - Shortcut key: `Ctrl-Shift-I` in Firefox.
      - Show `data` 
        - `header` and `items`
        - Can open item and see `id` and `label`
        - Great for seeing what is happening in your app and debugging.
      - Can also test code by changing values
        - Change the `header` to check reactivity.
        - Change a `label`
        - Add an `item`
          - `{ "id": 4, "label": "1 cake" }`
            - A few quirks...
              - Need to quote the `id` and `label` here.
              - Also need to use double quotes.
  - Some other little quirks:
    - Objects and arrays will have trailing commas when split across multiple lines.
      - E.g. after each object in `items` array.
      - But not after `labels`
        - Unless they are long and split the line.
        - Demo by changing a label to be longer and reformat.
          - Reformat `Shift-Ctrl-I` in VSCodium.
      - This is just intended to help prevent you from forgetting to add them later if you add more items to an object or an array.
    - Quotes for string values:
      - In the `<template>` 
        - HTML strings are in `" "` (double quotes).
      - In the `<script>` strings are in `' '` (single quotes).
        - We can nest quotes.
        - Change a label to quote a word with double quotes.
      - This is just a convention. Other projects may do it differently.
      - If you mix it up, auto-format will usually fix it.
        - Change an HTML attribute to use `' '` and reformat.
        - Change a `label` to use `" "` and reformat.

## Extending the Tutorial

- Work on the Hands-on activity.
  - Solution is in: `modules/farm_fd2_school/03-Vue1-Activity-Soln`

## Setup for 03-Vue1-Homework

- You will work in `modules/farm_fd2_school/src/entrypoints/Vue1/App.vue`
  - Visit FD2 School -> Vue1
    - The goal will be to render the elements from Vue data using `v-for`
      - The options for the "Crop"
      - The rows of the table.
      - The options for the "Units"
    - When you are done, the page will look and act pretty much exactly the same. It will just be using Vue `data` and `v-for` instead of using static HTML.
      - This is moving us toward a page that will respond to user actions.
  - Show the `App.vue` 
    - The `<template>` has the 02-HTML-CSS-Application solution code we saw earlier.
    - You will:
      - Add Vue code in the `<script>` tag.
      - Modify the `<template>` to use the Vue data.

## What to Do
  - Do the 03-Vue1-Application assignment.
    - Review and study the 03-Vue1-Tutorials as necessary.
  - Do the 04-Vue2-Tutorials assignment.
  - These don't have to be perfect... 
    - They don't have to be complete...
    - But they do have to be submitted.
    - Recommend that you time box them... 
      - Work for 1-2 hours then make a PR for what you have.
      - Then if you have more time continue working.
    - Each week you'll get solutions to the prior week so you can start those assignments in a working state and keep moving forward.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)