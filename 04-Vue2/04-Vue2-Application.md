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

SHOULD NOT HAVE TO EXPLAIN AS MUCH HERE SINCE IT IS IN THE TUTORIALS.

Use `v-model` to bind the `<input>` elements to attributes in the Vue `data` as follows:
1. For the `date` input:
   1. Remove the `value` attribute from the `date` input in the `<template>`.
   2. Add a `date` attribute to the Vue data in the `<script>` (e.g. `date: '2019-06-15'`)
   3. Use `v-model` to bind the value of the date input in the `<template>` to the value of the `date` attribute in the Vue `data` in the `<script>`.
   4. Use the Vue Devtools to confirm that:
      - Changing the value of the `date` attribute in the Vue `data` changes the date in the `date` input in the user interface.
      - Changing the date in the user interface changes the value of the `date` attribute in the Vue `data.`
        - Note: You may need to click the refresh icon in the upper right corner of the Vue Devtools to see changes in the `date` attribute after changing the input in the user interface.
2. Use a similar approach to bind the value of the following inputs to new attributes in the `Vue` data.
   - The `<select>` for the "Crop".
     - Ensure that "RADISH" is initially selected as it was before.
   - The `<input>` for the "Quantity".
     - Ensure that the quantity is initially set to 1 as it was before.
   - The `<select>` for the "Units" for the "Quantity".
     - Ensure that the "BUNCH" is initially selected as it was before.
   - The `<textarea>` for the "Comment box".
     - Ensure that the "Comment" is initially empty (i.e. displays the placeholder) as it did before.
3. Be sure to use the Vue Devtools to ensure that each binding is working correctly.
4. Commit the changes to your feature branch with a meaningful commit message.


## Binding the Radio Buttons

WE MAY NOT HAVE WHAT WE NEED HERE? CHECK THE VIDEO AGAIN

1. Bind the index of the selected radio button in the plant table to a new attribute in the Vue `data`.
   - For example if the plant in "D" is selected then the value of the new data attribute should be 0. Similarly, if the plant in "GHANA-2" is selected then the value of the data attribute should be 1.
   - Hint: Try asking your favorite AI how to bind the index of the selected radio button in a group to a data value in Vue.
2. Use the Vue Devtools to confirm that your binding works when you change the selection in the UI and when you change the index in the `data`.
3. Commit the changes to your feature branch with a meaningful commit message.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)