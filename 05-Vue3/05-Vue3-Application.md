# 05 - Vue3 - Application

In this assignment you will modify the prototype Harvest form so that it's content can be reset and so that unnecessary user interface elements are hidden when they are not needed.

## Preliminaries

1. Restart your FarmData2 Development Environment.
2. Synchronize your `development` branch with the upstream to add the starter code for this assignment to your repository.
3. Rebuild the `fd2_school` module.
4. Use the "FD2 School" menu to navigate to the "Vue3" page.
   - This page will contain a working solution to the Vue2 Application assignment.
   - If you do not see the "Vue3" menu or a working solution to the Vue2 Application assignment, check that you have performed steps 2 and 3 correctly and try again.
5. Create a new feature branch from `development` and switch to it for your work on this assignment.
6. Open the FarmData2 folder in VSCodium.
7. Find the `modules/farm_fd2_school/src/entrypoints/Vue3/App.vue` file and open it.
   - You will modify the code in the `App.vue` file to complete this assignment.

## Resetting the Form

In the previous Application you assigned an event handler to the "Reset" button that printed a message in the console when the button was clicked. Now that you have learned how to create methods, you can have the "Reset" button actually reset the values in the form.

1. Update the Harvest form so that when the "Reset" button is clicked the the values in the inputs are reset as follows:
   - The "Date" is reset to June 15, 2019.
   - No "Crop" is selected.
     - Hint: Ask your favorite AI how to ensure that no option is selected in an HTML select when using Vue.
   - No plants in the table are selected (i.e. no radio button is selected).
   - The "Quantity" to be harvested is 1.
   - No "Unit" is selected for the harvest.
   - The "Comment" is blank (i.e. shows the placeholder text).
2. Test your implementation to be sure it resets all of the inputs as required when the "Reset" button is clicked.
3. Commit the changes to your feature branch with a meaningful commit message.

## Select no Crop or Unit by Default

Currently when a user first visits the Harvest form there are default values for the crop being harvested ("RADISH") and the harvest unit ("BUNCH"). Setting those was good practice and helped us learn a little more about Vue. But it probably makes more sense to have the user select the crop and harvest unit rather than having these defaults set.

1. Change the Vue data so that no harvest "Crop" is selected when the page is initially loaded. 
   - Hint: Setting the data value bound to a `select` input to an empty string `''` or to `null` causes no item to be selected.
2. Rebuild the school module and reload the page to ensure that no crop is selected by default.
3. Change the Vue data so that no harvest "Unit" is selected when the page is initially loaded.
4. Rebuild the school module and reload the page to ensure that no unit is selected by default.
5. Commit the changes to your feature branch with a meaningful commit message.

## Hide Page Elements when no Crop is Selected

Now when the Harvest form is loaded or reset no crop will be selected. However, the table of plants, the harvest "Quantity" input, the "Unit" select and the "Comment" textarea are still visible in the page. But these elements are not useful when no crop has been selected for harvest. So let's hide them unless a crop is selected. Note that it might also be sensible to hide the "Submit" and "Reset" buttons in this situation, but we'll be doing something different with them in a later topic, so they should remain visible.

1. Modify the Harvest form so that the table of plants, the "Quantity" input the "Unit" select and the "Comment" text area are not visible when no crop is selected (i.e. after a reset).
2. Test your implementation to be sure the "Quantity" input the "Unit" select and the "Comment" text area are only visible when a crop is selected.
3. Commit the changes to your feature branch with a meaningful commit message.

## Checklist

- When the page is reloaded:
  - No "Crop" is selected.
  - The table, quantity, units and comment are hidden.
- Selecting a "Crop" reveals the:
  - "Plants" table with no row selected.
  - "Quantity" input with value 1.
  - "Unit" select with no unit selected.
  - "Comment" box with the placeholder text.
- Clicking "Reset":
  - Sets the "Date" to June 15, 2019.
  - Clears any selected "Crop".
  - Clears any selected row in the "Plants" table.
  - Sets the "Quantity" to 1.
  - Clears any selected "Unit".
  - Clears any entered "Comment"
  - Hides the "Plants" table, "Quantity" input, "Unit" select and "Comment" box.

## Turning In Your Work

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your origin repo.
3. Go to your origin repo on GitHub.
4. Make a PR to the `development` branch in the upstream repository.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR to ensure that you have only made changes in the `modules/farm_fd2_school/src/entrypoints/Vue3` directory. Make any necessary changes, commit them to your feature branch and push it again to update the PR.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)