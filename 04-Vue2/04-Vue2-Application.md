# 04 - Vue2 - Application

In this assignment you will 

## Preliminaries

1. Restart your FarmData2 Development Environment.
2. Synchronize your `development` branch with the upstream to add the starter code for this assignment to your repository.
3. Rebuild the `fd2_school` module.
4. Use the "FD2 School" menu to navigate to the "Vue2" page.
   - This page will contain a working solution to the Vue1 Application assignment.
   - If you do not see the "Vue2" menu or a working solution to the Vue1 Application assignment, check that you have performed steps 2 and 3 correctly and try again.
5. Create a new feature branch from `development` and switch to it for your work on this assignment.
6. Open the FarmData2 folder in VSCodium.
7. Find the `modules/farm_fd2_school/src/entrypoints/Vue2/App.vue` file and open it.
   - You will modify the code in this file `App.vue` file to complete this assignment.

## Binding `<input>` values with `v-model`

The first tutorial showed that the value of an `<input>` element can be bound to the value of an attribute in the `data` using Vue's `v-model` directive. When this is done, the value in the input and the value in the `data` stay in synch. If the input is changes, the data changes and vice versa.

1. Use `v-model` to bind the `date` `<input>` element to a new property in the Vue `data` as follows:
   1. Remove the `value` attribute from the `date` input in the `<template>`.
   2. Add a `date` property to the Vue data in the `<script>` (e.g. `date: '2019-06-15'`)
   3. Use `v-model` to bind the value of the date input in the `<template>` to the value of the `date` property in the Vue `data` in the `<script>`.
   4. Use the Vue Devtools to confirm that:
      - Changing the value of the `date` property in the Vue `data` changes the date in the `date` input in the user interface.
      - Changing the date in the user interface changes the value of the `date` property in the Vue `data.`
        - Note: You may need to click the refresh icon in the upper right corner of the Vue Devtools to see changes in the `date` property after changing the input in the user interface.
2. Bind the `<select>` input for the "Crop" to a new property in the Vue `data`.
   - Ensure that "RADISH" is initially selected as it was before.
3. Bind the "Quantity" `<input>` to a new property in the Vue `data`.
   - Ensure that the quantity is initially set to 1 as it was before.
4. Bind the `<select>` input for the "Units" of harvest to a new property in the Vue `data`.
   - Ensure that the "BUNCH" is initially selected as it was before.
5. Bind the "Comment box" `<textarea>` to a new property in the Vue `data`.
   - Ensure that the "Comment" is initially empty (i.e. displays the placeholder) as it did before.
6. Be sure to use the Vue Devtools to ensure that each binding is working correctly.
7. Commit the changes to your feature branch with a meaningful commit message.

## Binding the Radio Buttons

1. Bind the radio buttons in the table to a new property in the Vue `data` such that the value of the new property gives the index of the associated plant in the `plantList` array.  For example, if the radio button in the first row is selected the value of the new `data` property should be `0` because the information for that row is in index 0 of the `plantList` array.
   - Hint 1: Add an `index` to the `v-for` that renders the table. Then use `v-bind` set the value of each of the radio buttons to be the `index`. Then use `v-model`.
   - Hint 2: Try asking your favorite AI how to bind the index of a radio button to a data property in Vue.
2. Be sure to use the Vue Devtools to ensure that the binding is working correctly.
3. Commit the changes to your feature branch with a meaningful commit message.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)