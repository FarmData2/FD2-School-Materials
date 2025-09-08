# 02 - Vue1 - Application

In this assignment you will refactor the static HTML/CSS harvest form created in the previous assignment to use Vue's _data binding_ and _list rendering_ features. You (mostly) won't be changing the appearance or functionality of the page in this assignment, just how it is implemented behind the scenes in the `App.vue` file.

## Preliminaries

1. Restart your FarmData2 Development Environment.
2. Synchronize your `development` branch with the upstream to add the starter code for this assignment to your repository.
3. Rebuild the `fd2_school` module.
4. Use the "FD2 School" menu to navigate to the "Vue1" page.
   - This page will contain a working solution to the HTML-CSS Application assignment.
   - If you do not see the "Vue1" menu or a working solution to the HTML-CSS Application assignment, check that you have performed steps 2 and 3 correctly and try again.
5. Make a branch from `development` for your work on this assignment.
6. Open the FarmData2 folder in VSCodium.
7. Find the `modules/farm_fd2_school/src/entrypoints/Vue1/App.vue` file and open it.
   - You will modify the code in this file `App.vue` file to complete this assignment.

## Binding `<input>` values with `v-model`

The first tutorial showed that the value of an `<input>` element can be bound to the value of an attribute in the `data` using Vue's `v-model` directive. When this is done, the value in the input and the value in the `data` stay in synch. If the input is changes, the data changes and vice versa.

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

## Generating the Crops from `data`

Eventually we will want to read the list of crops that appear in the "Crop" select element from the FarmData2 database.  This will be much easer, if the options in that element are generated dynamically from data using Vue's data binding (i.e. `{{ }}`) and list rendering capabilities (i.e. `v-for`)

1. Change the page so that the list of crops in the "Crop" select element is generated from an array of strings in the Vue instance `data` instead of being hard coded in the `<template>`.
   - Hint: You can use the crop name as the `key` in your `v-for`.
2. Commit the changes to your feature branch with a meaningful commit message.

## Generating the Plant table from `data`

Similar to the list of crops that can be harvested, the data in the table showing the plants for the selected crop will eventually be read from FarmData2. To prepare for that let's generate the rows of that table dynamically using Vue's data binding and list rendering capabilities too.

1. Change the page so that the list of plants in the table is generated from an array of objects in the Vue instance `data` instead of being hard coded in the `<template>`.
   - The plant objects should include attributes and values for:
     - `id`, `date`, `location`, `bed`.
   - You should omit the `id` and `value` attributes from the radio button for now. You'll add those back in later.
2. Commit the changes to your feature branch with a meaningful commit message.

## Generating the Units from `data`

1. Change the page so that the list of units in the "Units" select element to the right of "Quantity" is generated from an array of strings in the Vue instance `data` instead of being hard coded in the `<template>`.
2. Commit the changes to your feature branch with a meaningful commit message.

## Optional Challenge

1. Bind the index of the selected radio button in the plant table to a new attribute in the Vue `data`.
   - For example if the plant in "D" is selected then the value of the new data attribute should be 0. Similarly, if the plant in "GHANA-2" is selected then the value of the data attribute should be 1.
   - Hint: Try asking your favorite AI how to bind the index of the selected radio button in a group to a data value in Vue.
2. Use the Vue Devtools to confirm that your binding works when you change the selection in the UI and when you change the index in the `data`.
3. Commit the changes to your feature branch with a meaningful commit message.

## Checklist

- The "Date", "Crop", "Quantity", "Units" and "Comment box" inputs are bound to attributes in the Vue `data` and have the correct initial values.
- The options in the "Crop" select are rendered from an array of strings in Vue `data` using `v-for`.
- The rows in the "Plants" table are rendered from an array of objects in the Vue `data` using `v-for`.
- The options in the "Units" select are rendered from an array of strings in the Vue `data` using `v-for`.
- Optionally the index of the selected plant in the table is bound to an attribute in the Vue `data`.

## Turning In Your Work

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your origin repo.
3. Go to your origin repo on GitHub.
4. Make a PR to the `development` branch in the upstream repository.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR to ensure that you have only made changes in the `modules/farm_fd2_school/src/entrypoints/Vue1` directory. Make any necessary changes, commit them to your feature branch and push it again to update the PR.

