# 06 - Vue4 - Application

In this assignment you will modify the prototype Harvest form so that the "Submit" button will only be enabled when the form contains valid content and so that the plants in the table appear in sorted order by date.

## Preliminaries

1. Restart your FarmData2 Development Environment.
2. Synchronize your `development` branch with the upstream to add the starter code for this assignment to your repository.
3. Rebuild the `fd2_school` module.
4. Use the "FD2 School" menu to navigate to the "Vue4" page.
   - This page will contain a working solution to the Vue3 Application assignment.
   - If you do not see the "Vue4" menu or a working solution to the Vue3 Application assignment, check that you have performed steps 2 and 3 correctly and try again.
5. Create a new feature branch from `development` and switch to it for your work on this assignment.
6. Open the FarmData2 folder in VSCodium.
7. Find the `modules/farm_fd2_school/src/entrypoints/Vue4/App.vue` file and open it.
   - You will modify the code in the `App.vue` file to complete this assignment.

## Disabling the "Submit" Button

The "Submit" button on the Harvest form should only be disabled if the form does not contain all of the necessary information for creating a harvest log.  To create a valid harvest log in FarmData2 requires a date, a crop, a selected plant, a quantity that was harvested and the unit for the harvest. A comment may be present but it is not required.

1. Modify the Harvest form so that the "Submit" button becomes enabled only when the user has provided all of the required information for the harvest log.
   - Hint 1: This is very similar how you disabled the "Save" button in the tutorials and the "High Priority" checkbox in the hands-on activity.
   - Hint 2: You can use the logical operators (`&&`, `||`, `!`) in a computed property to create an expression that indicates if all of the Vue `data` properties for the required inputs have valid values.
   - Hint 3: The values of the `data` properties are set by HTML inputs that only allow valid inputs, so we know that if these `data` properties have a value that is not `''` then their value is valid.
2. Use the Vue Devtools and the Harvest form page to test your changes.
   - Hint: You can "Clear" the date by clicking on the calendar, and you can delete the quantity by clicking in the text field.
3. Commit the changes to your feature branch with a meaningful commit message.

## Sorting the Plants by Date

When harvesting a particular crop it will often make sense to harvest from the most mature plants. The user interface of the Harvest form should facilitate this by listing the plants in the table with the oldest plants at the top.

1. Change the dates of the plant objects in the `plantList` so that they are not already in sorted order.  You can pick whatever dates you like.
2. Modify the Harvest form so that plants in the table are sorted by date with the oldest plants at the top and the youngest plants at the bottom.
   - Hint 1: The technique for doing this will be similar to the way the shopping list was reversed in the tutorials and sorted by value in the hands-on activity. 
   - Hint 2: Try asking your favorite AI "How can I sort an array of objects with this format { id: 2, date: '04/02/2019', location: 'GHANA', bed: 'GHANA-2' } by date in JavaScript."
3. Use the Vue Devtools and the Harvest form page to test your changes.
4. Commit the changes to your feature branch with a meaningful commit message.

## Checklist

- "Submit" button is disabled any time the form data is not valid.
- Plants appear in order from oldest to newest in the table.

## Turning In Your Work

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your origin repo.
3. Go to your origin repo on GitHub.
4. Make a PR to the `development` branch in the upstream repository.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR to ensure that you have only made changes in the `modules/farm_fd2_school/src/entrypoints/Vue4` directory. Make any necessary changes, commit them to your feature branch and push it again to update the PR.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)