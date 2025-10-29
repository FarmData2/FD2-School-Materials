# 09 - FD3 - Application

In this assignment you will replace some additional components in the Harvest form with components from FarmData2.

## Preliminaries

1. Restart your FarmData2 Development Environment.
2. Synchronize your `development` branch with the upstream to add the starter code for this assignment to your repository.
3. Use the "FD2 School" menu to navigate to the "FD3-Application" page.
   - This page will contain a working solution to the FD2 Activity assignment, which is also the starter code for this assignment.
4. Create a new feature branch from `development` and switch to it for your work on this assignment.
5. Open the FarmData2 folder in VSCodium.
6. Find the `modules/farm_fd2_school/src/entrypoints/FD3_Application/App.vue` file and open it.
   - You will modify the code in this file `App.vue` file to complete this assignment.
7. Start the documentation server as referencing the documentation for the components you will be using will be helpful.





**** MAY NEED TO REBUILD DOCS ******





## The `CommentBox` Component

1. Change the comment box in the Harvest form to be a FarmData2 `CommentBox` component instead of an HTML `textarea`.
2. Rebuild the `school` module, reload the page.
3. Confirm that the new comment box works.
4. Commit the changes to your feature branch.

## The `SubmitResetButtons` Component

- replace submit and reset buttons

## The `NumericInput` Component

- replace numeric input

## The `CropSelector` Component

SOME CHALLENGE IN GETTING THIS TO WORK...

1. Change the select for the crop in the Harvest form to be a FarmData2 `CropSelector` component instead of an HTML `select`.
2. Rebuild the `school` module, reload the page.
3. Confirm that the new crop selector works.

NOTICE THE PAYLOAD OF THE update:select EVENT!!!
- Just the name...
RIPPLING CHANGES HERE BECAUSE CROP IS JUST A NAME NOW.
- 2 places in the `watch`
- In the message if no plants exist in the template.


## Checklist

- blah

## Turning In Your Work

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your origin repo.
3. Go to your origin repo on GitHub.
4. Make a PR to the `development` branch in the upstream repository.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR to ensure that you have only made changes in the `modules/farm_fd2_school/src/entrypoints/FD2` directory. Make any necessary changes, commit them to your feature branch and push it again to update the PR.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)