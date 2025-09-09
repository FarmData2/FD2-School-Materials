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

## Generating the Crops from `data`

Eventually we will want to read the list of crops that appear in the "Crop" select element from the FarmData2 database.  This will be much easer, if the options in that element are generated dynamically from data using Vue's data binding (i.e. `{{ }}`) and list rendering capabilities (i.e. `v-for`)

1. Change the page so that the list of crops in the "Crop" select element is generated from an array of strings in the Vue instance `data` instead of being hard coded in the `<template>`.
   - The list of crops should be the same as they were before. But it is not necessary that "RADISH" is selected by default.
   - Hint: You'll need to set a `key` in your `v-for`. Because the crop names are unique, you can use it as the `key`.
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

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)