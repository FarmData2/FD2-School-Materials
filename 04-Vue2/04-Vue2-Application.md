# 04 - Vue2 - Application

In this assignment you will bind the values of the user input elements to `Vue` data

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
   2. Add a `date` property to the Vue `data` in the `<script>` so that the initial date is June 15, 2019 (`date: '2019-06-15'`).
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
   - Hint: This is very similar to what you did in the Hands On activity. But, here you want to use the `index` of the `v-for` as the `value` instead of the `id` of the `item`.
2. Be sure to use the Vue Devtools to ensure that the binding is working correctly.
3. Set the initial value of the `data` property such that no radio button will be selected when the page is loaded.
   - Hint: Use a value that will never be a valid `index` in the `v-for`.
3. Commit the changes to your feature branch with a meaningful commit message.

## Adding Event Handlers

In JavaScript the `console.log` command can be used to display a message in the browser developer tools Console.  For example:
```
Console.log("This is a test, this is only a test.")
```
This type of output can be useful during the initial stages of development and in debugging.  We'll use it here to check that we can handle events from our "Submit" and "Reset" buttons.

1. Add a `v-on` handler to the "Submit" button that displays the message "Submit was clicked" in the console.
   - Rebuild
   - Reload the page (Use SHIFT+reload)
   - Open the Devtools
   - Go to the "Console"
   - Then click the "Submit" button to ensure that the message is displayed.
2. Add a `v-on` handler to the "Reset" button that displays the message "Reset was clicked" in the console.

## Checklist

- The following `<input>` elements are bound to Vue `data` properties:
  - "Date" with the initial date of June 15, 2019
  - "Crop" select with "RADISH" selected initially
  - "Quantity" input with initial value of 1
  - "Units" select with "BUNCH" selected initially
  - "Comment Box" displaying the placeholder text (i.e. initially empty)
  - All radio buttons with no button selected initially
- Clicking the "Submit" button displays the "Submit was clicked." message in the Devtools console.
- Clicking the "Reset" button displays the "Reset was clicked." message in the Devtools console.

## Turning In Your Work

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your origin repo.
3. Go to your origin repo on GitHub.
4. Make a PR to the `development` branch in the upstream repository.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR to ensure that you have only made changes in the `modules/farm_fd2_school/src/entrypoints/Vue2` directory. Make any necessary changes, commit them to your feature branch and push it again to update the PR.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)