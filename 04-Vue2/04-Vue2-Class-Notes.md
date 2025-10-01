# 04 - Vue2 - Class Notes

## Instructor ToDo Before Class

- Merge 
  - `04-Vue2-Tutorial-Soln`
  - `04-Vue2-Activity-Soln`
  - `04-Vue2-Application-Starter`

## Synchronize with `upstream` `development`

- Open dev environment (from a fork as a student)
- `cd FarmData2`
- Synch with `upstream.
  - `git switch development`
  - `git pull upstream development`
- Note the new directories that are added in `modules/farm_fd2_school`:
  - `04-Vue1-Tutorials-Soln`
  - `04-Vue1-Activity-Soln`
  - `src/entrypoints/04-Vue2`

## A Cautionary Note

- As you work I recommend that you commit regularly with good commit messages (as you have been) but then also push to your `origin` regularly.
  - Your file changes and commits are stored in the Codespace.
  - That is separate from your GitHub.
  - The push to `origin` puts the branch in your GitHub.
  - That acts as a backup just in case something happens to corrupt the Codespace.
    - This is rare, but it can happen.
    - You'll be able to get back all of the work that you have pushed.
    - But any changes that were not pushed would be lost.

## Review 03-Vue1-Application Solution

- The overall goal was to generate the page content from Vue `data` using `v-for` directives.
- Solution is in `modules/farm_fd2_school/src/entrypoints/04-Vue2/App.vue`
  - This is the solution to the `03-Vue1-Application` assignment.
  - It is also the starter code for the `04-Vue2-Application` assignment.
  - This directory was added by the `pull` of `development` from `upstream`
- Build the school module
  - `cd FarmData2`
  - `npm run build:school`
- Show the working page in the browser
  - Open `http://farmos` and visit "FD2 School" -> "Vue2".
  - Looks and acts just like it did before.
    - But behind the scenes the static HTML has been replaced with Vue code.
- Show the code in `modules/farm_fd2_school/src/entrypoints/Vue2/App.vue` in VSCodium.

### Adding the Vue Instance

- In the tutorials you created the Vue instance as:
  ```
  const shoppingListApp = Vue.createApp({
      data() {
        return {
          
        };
      },
    }).mount('#shopping-list');
  ```
- However, in the `Vue1` entrypoint you create the Vue instance between the `<script>` tags as follows:
  ```
  export default {
    data() {

    },
  };
  ```
  - This is similar to what you did in the tutorials but the syntax is slightly different. Doing it this way in FarmData2 allows us to keep the HTML, CSS and Vue code all neatly in a single file when building entrypoints.
    - This is called a Single File Component (SFC) in Vue.
    - The build process (`npm run build:school`) breaks the HTMl, CSS and script apart and combines them with some other code (the other files in the `Vue2` directory and elsewhere) that allows them to work inside of farmOS.

### Generating the "Crops" `<option>`s from `data`

- I added an array of strings to the Vue `data`
  - `cropList: cropList: ['ARUGULA', 'ASPARAGUS', 'BEAN', 'RADISH'],`
  - Notice that I didn't create an array of objects here.
    - It wouldn't be wrong to do that.
    - It just isn't really necessary since all we really want is the name of the crop and they will all be unique, we don't need an `id`.
- Then in the `<select>` I added a `v-for` to the `<option>`
  ```
  <select id="harvest-crop">
    <option
      v-for="crop in cropList"
      v-bind:key="crop"
    >
      {{ crop }}
    </option>
  </select>
  ```
  - The `<option>` is the thing that we want to repeat.
    - I.e. We want one `<option>` for every `crop` in the `cropList`.
    - So the `v-for` goes on the `<option>` element.
    - The crop names in `cropList` are unique, so we can `v-bind` the `crop` as the `key` as well.
  - Then the `{{ crop }}` uses the name of the crop from `cropList` as the content of the `<option>`.

### Generating the Plant table from `data`

- Show the code from `04-Vue2`
- The approach for generating the table of plants from the Vue `data` is similar and matched more closely what was shown in the tutorial.
- I added an array of objects to the Vue `data`:
  ```
  export default {
    data() {
      ...
      plantList: [
        { id: 1, date: '04/02/2019', location: 'D', bed: '' },
        { id: 2, date: '04/02/2019', location: 'GHANA', bed: 'GHANA-2' },
        { id: 3, date: '04/02/2019', location: 'GHANA', bed: 'GHANA-4' },
        { id: 4, date: '06/05/2019', location: 'GHANA', bed: 'GHANA-4' },
      ],
      ...
    },
  }
  ```
    - Note: The `...` is used to represent omitted statements. The full code including the omitted statements can be seen in the provided solutions.
  - Here each object has 4 properties that hold the important information about the plant:
    - `id` - a unique identifier for the plant.
    - `date` - the date the plant was planted.
    - `location` - where the plant is located.
    - `bed` - the bed within the location where the plant is located.
  - Note that:
    - With objects we can have whatever properties we need.
      - These are just like fields in objects in other languages such as Java, Python, C/C++ ect.
    - Using multiple properties here is similar to the way the hands-on activity had you split the `quantity` and `label` in the shopping list `items`.
- We then want our `<table>` to contain one row for each object in the `plantList`.
  - So we use the `v-for` on the `<tr>` element.
    ```
    <tr
      v-for="plant in plantList"
      v-bind:key="plant.id"
    >
      ...
    </tr>
    ```
  - And then in that row we use Vue's `{{ }}` to insert the appropriate properties from object into the columns (`<td>`s) of the row. 
    ```
      <td>
        <input
          type="radio"
          name="harvest-plant"
        />
      </td>
      <td>{{ plant.location }}</td>
      <td>{{ plant.bed || '' }}</td>
      <td>{{ plant.date }}</td>
    ```
    - Note that the first `<td>` adds the radio button in the first column and doesn't use any data from the object.
    - Note: The `{{ plant.bed || '' }}.
      - This was added so that the objects for plants that are not in a specific bed could omit the `bed` property instead of setting it to `''`.
      - This is not strictly necessary, but is an defensive programming strategy that you see frequently in Vue / Javascript code that can help prevent potential issues later.

### Generating the Units from `data`

- Generating the Units from the Vue `data` is done in exactly the same way as was done for the crops, so we'll skip over that here.

## Tutorials T04 Solution

- Show the working page in the browser.
  - Visit `modules/farm_fd2_school/04-Vue2-Tutorials-Soln`
    - Show that we can add an item to the list by:
      - clicking "Save".
      - pressing "enter" in the input field.
- There were two parts that work together to make this happen:
  - We bind the HTML inputs to properties in the Vue `data` by using Vue's `v-model` directive.
  - We assign code to run when the user clicks "Save" or presses "enter" in the input field by using Vue's `v-on` directive.
- Let's look at each of these pieces in turn.

### Binding HTML Inputs into Vue `data`

- To bind the inputs into the Vue `data` we add a property to the Vue `data` for each input that we want to bind:
  ```
  data() {
    return {
      ...
      newItem: '',
      newItemHighPriority: false,
      ...
    }
  },
  ```
- Then we also use `v-model` in the HTML elements in the `<template>` to bind the `value` of the input to the Vue `data` properties.
  - For the "New Item" input field:
    ```
    <input
      ...
      v-model="newItem"
      type="text"
      placeholder="Add an item"
    />
    ```
  - For the "High Priority" check box:
    ```
    <input
      type="checkbox"
      v-model="newItemHighPriority"
    />
    ```
- Demo the binding using the Vue Devtools
  - `Shift+Ctrl+I` shortcut
    - Show dock to bottom or dock to right options.
  - Can see that the Vue `data` contains properties:
    - `newItem` and `newItemHighPriority`
    - as well as all of the other properties we already had.
  - Can see that the value of:
    - `newItem` updates as we type in the field.
    - `newItemHighPriority` updates when we click the checkbox.
  - Remember that sometimes you may need to refresh the Vue Devtools to see changes in the `data`.
  
### Responding to User Events

- To respond to user events we attach code (an _event handler_) to those events using Vue's `v-on` directive.
  - For the "Save" button:
    ```
    <button
      v-on:click="items.push({id: items.length + 1, label: newItem})"
      class="btn btn-primary"
    >
    ```
  - For the "New Item" input field:
    ```
    <input
      v-on:keyup.enter="items.push({id: items.length + 1, label: newItem})"
      v-model="newItem"
      type="text"
      placeholder="Add an item"
    />
    ```
  - Both of these event handlers do the same thing.
    - They create a new object and add it to the end of the `items` array in the Vue `data`.
      - `push` is a Javascript method that can be called on an array and will add whatever is passed to it to the end of the array.
        - In this case the object `{id: items.length + 1, label: newItem}` is passed to the `push` method to be added to the end of the `items` array.
  - Show the effect in the Vue Devtools.
    - Reload the page.
    - Point out the 3 elements in the `items` array.
    - Type in a new item and click "Save"
      - It immediately appears in the list.
    - Show that there is now a 4th element in the `items` array.
      - Notice that:
        - The value of the `label` property has the value that we typed.
          - That is because it was `v-bound` to `newItem` and `newItem` was set as the value of the `label` property in the object that was pushed.
        - The value of the `id` property is 4.
          - That is because when we clicked "Save" there were 3 elements in the list, so `list.length` was 3 and the value of the `id` property was set to `list.length + 1`, which is 4.
            - This is just a convenient way to ensure that each item in the list has a unique `id` value that we could use for the `key` in the `v-for`.
    - So what made the displayed list update? We didn't tell it to do that!
      - Remember that in the `<template>` we have code that uses `v-for` to render the list of items in the page.
        ```
        <ul>
          <li
            v-for="item in items"
            v-bind:key="item.id"
          >
            {{item.label}}
          </li>
        </ul>
        ```
      - What happens is that Vue notices that the `items` array has changed.
        - It knows that the list depends on `items`.
        - So it re-renders the list into the page.
        - If there were other content on the page that also used `items` in some way, that content would also be re-rendered.
      - This is Vue's _reactivity_ at work.
        - This is exactly the same thing that happened when you changed the `header` or added or removed objects from `items` using the Vue Devtools.
        - Now it is happening because the code has changed `items`.

## Some Additional Points

- The Tutorials introduced the `<form>` element.
  - Many web pages and Vue apps use the `<form>` element.
  - However, FarmData2 does not because we want more control over when and how the entered data is submitted.
- FarmData2 uses the long version of `v-on` instead of `@` and the linters will change it when you commit.
- If you make syntax errors in your Vue code the page may:
  - Load but not work without any direct indication why.
  - Appear as a blank page with out any direct indication why.
  - The Devtools Console can be helpful here.
    - Demo this using the tutorial solution page.
    - Change `push` to `posh` in `v-on` for the "Save" button.
      - Reload the page.
      - It renders fine but clicking the "Save" button doesn't do anything.
      - Error message in the Console indicates `posh` is not a function.
         - Pretty helpful.
      - Fix the mistake.
    - Change `v-for` to `v-fort` in the `<li>`
      - Reload the page.
      - It does not render - blank page.
      - This is because the problem here is with Vue code and it doesn't know what to do to render the page.
      - Error message in the Console is a little less helpful.
      - Sometimes they will be completely unhelpful, particularly when working in the FarmData2 entrypoints.
      - But know if you get a blank page and an error in the Console, it likely means that you have problem in your Vue code.
- Commenting out the most recently added code is often a good way to check this.
  - Imagine the page had been working fine and we just added the `<li>` with the `v-for` and we don't see the mistake just by looking.
  - We can comment out that new code and reload (or rebuild) the page to see if it starts working again.
    - If it does, we know that the newly added code was the problem.
  - The key combination `Ctrl+/` is a shortcut that toggles the active line, or selected lines, as a comment.
    - Comment out the `<li>`
    - Reload the page.
    - Page renders, but the list isn't there because it has no items because we commented out the `<li>`.
    - This means we found the code containing the problem.
- HTML comments vs Vue/Javascript comments:
  - When I comment out the `<li>` it uses an HTML comment.
    - `<!-- -->`
  - When I comment out Vue or JS code it will use a JS comment.
    - `//`
  - Block comments also work in Vue/JS code.  The shortcut key just doesn't use them.
    ```
    /*
     Block comment.
     */ 
    ```

## Extending the Tutorial

- Work on the Hands-on activity.
  - Solution is in: `modules/farm_fd2_school/04-Vue2-Activity-Soln`

## Setup for 04-Vue2-Homework

- You will work in `modules/farm_fd2_school/src/entrypoints/Vue2/App.vue`
  - Visit "FD2 School" -> "Vue2"
  - The goals will be to:
    - Bind the user inputs to Vue `data` properties.
    - Add event handlers to the "Submit" and "Reset" buttons.
      - These won't do anything particularly useful yet.
      - But they are a setup for the next topic where we'll see how to do some useful stuff.
    - When you are done, the page will look and act pretty much exactly the same.

## What to Do
  - Do the 04-Vue2-Application assignment.
    - Review and study the 04-Vue2-Tutorials as necessary.
  - Do the 05-Vue3-Tutorials assignment.
  - The HW and Tutorials assignments...
    - don't have to be perfect... 
    - don't have to be complete...
    - But they do have to be submitted.
    - I recommend that you time box them... 
      - Work for 1-2 hours then make a PR for what you have.
      - Then if you have more time continue working.
    - Each week you'll get solutions to the prior week so you can start those assignments in a working state and keep moving forward.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)
