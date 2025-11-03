# 08 - FD2 - Application

In this assignment you will modify the prototype Harvest form to make further use of the `farmosUtil` library.  You will use `farmosUtil` functions to:
- fetch the plants when a crop is selected.
- fetching the units that should appear in the "Unit" select for the selected crop.
- have clicking the submit button use the data entered in the Harvest form to create a harvest log in farmOS.

## Preliminaries

1. Restart your FarmData2 Development Environment.
2. Synchronize your `development` branch with the upstream to add the starter code for this assignment to your repository.
3. Use the "FD2 School" menu to navigate to the "FD2-Application" page.
   - This page will contain a working solution to the FD2 Activity assignment, which is also the starter code for this assignment.
   - If you do not see the "FD2" menu or a working solution to the FD2 Activity assignment, check that you have performed steps 2 and 3 correctly and try again.
5. Create a new feature branch from `development` and switch to it for your work on this assignment.
6. Open the FarmData2 folder in VSCodium.
7. Find the `modules/farm_fd2_school/src/entrypoints/FD2-Application/App.vue` file and open it.
   - You will modify the code in the `App.vue` file to complete this assignment.

## Fetching the Plants with `farmosUtil`

Currently the code in the `watch` for `crop` changes still uses `fetch` directly to get the plants for the table.  While this works, using a `farmosUtil` function would be a better choice. Let's fix that.

1. Go to the documentation for the `farmosUtil` library.
   - Hint: Remember to run the documentation server using `npm run docs:view`.
2. Find the function that will get all of the plant assets based on things like the location, beds, crop, etc.
   - Hint: The function has to do with plants.
3. Modify the code in `App.vue` so that the pants for the selected crop are fetched using the `farmosUtil` function you found instead of by using `fetch`.
   - Hints: 
     - Replace the code in the `watch` for `crop`.
     - When calling the function you'll need to set the `cropName` parameter. However, because it is the third parameter you will need to provide the default values for the `locationName` and `checkedBeds` parameters and then provide the value for the `cropName`.
     - The default values for the parameters are given in the documentation.
     - The last two parameters `isInGround` and `isInTrays` can be omitted and their default values will be used.
4. Rebuild the `school` module and confirm that the page still works as expected.
5. Commit your changes to your feature branch.

## Setting the Harvest Units

Currently, when you select a crop the list of plants in the table is updated to show the plants that are available for harvest. For example, of you select "BEAN" all of the "BEAN" plants will be displayed in the table. However, the options in the "Unit" select remain "BUNCH", "EACH", and "POUND" regardless of the crop that is selected.

You know from 07-FD1-Application that each crop in FarmData2 has specific units in which it can be harvested. These are the _Harvest unit_ and the _Harvest unit conversions_ that you saw both in the farmOS user interface when you looked at the "Plant type" taxonomy terms and via the `taxonomy_term--plant_type` API endpoint. The goal for this section is ensure that the options in the "Unit" select agree with the selected crop.

1. Go to the documentation for the `farmosUtil` library.
2. Find the function that when given the name of a crop returns an array of the units in which the crop can be harvested.
   - Hint: These units have to do with "harvest" operations.
3. Modify the code in `App.vue` so that when the crop changes the options in the "Unit" select are set to be the units in which the selected crop can be harvested.
   - Hint: Add code to the `watch` on the `crop` property.
4. Rebuild the `school` module and reload the page.
5. Confirm that when you change the crop the options in the unit select also change.
   - Hints: 
     - When selecting "ARUGULA" the only unit should be "POUND".
     - When selecting "RADISH" the units should be "BUNCHES", "EACH", and "POUND".
6. Confirm that if you fill out the Harvest form and click "Submit" that a a quantity is still created with the correct values.
7. Commit your changes to your feature branch.

## Creating the Harvest Log

In the class we looked at the documentation for the `createHarvestLog` function and saw that it required a plant asset and a quantity object. You then used the `createStandardQuantity` object to create the necessary quantity. Let's now get the plant asset and create the harvest log.

1. Find the `submitForm` method in `App.vue` and review the provided code that creates the quantity object that we need.
2. Find the `farmosUtil` function that will get a plant asset when given its `id`.
3. Add code to the `submitForm` method that uses the function you found along with the `uuid` of the selected plant (i.e. `this.pickedPlant.uuid`) to fetch the full plant asset.
   - Tip: Use `console.log` to log the plant asset that you fetched so that you can check that it is correct before continuing.
4. Add code to the `submitForm` method that calls `createHarvestLog` to create the harvest log.
   - Hints: 
     - You have all of the information that you need to provide the parameters to the `createHarvestLog` function. The quantity and the plant asset are part of it. The rest of what you need is in the Vue `data`.
     - Hint: Look at the documentation for the `getPlantAssets` function in `farmosUtil` to see what is in the `pickedPlant` object.
5. Go to "Records" -> "Logs" -> "Harvest" in the farmOS user interface to confirm that you have correctly created the harvest log.
6. Commit your changes to your feature branch.

## Optional Challenge - Bug Fixes

1. Plants that are in a greenhouse (e.g. "CHUAU", "GHANA", "JASIME") may either be in seeding trays or in the ground. Plants that are in seeding trays are not ready to be harvested and shouldn't be listed in the table. Modify the code in `App.vue` so that only plants that are in the ground are shown.
   - Hints:
     - Look at the documentation for the `fetchPlantAssets` function.
     - When this works plants in "CHUAU" or "GHANA" should only appear in the table if they have associated beds.
2. Confirm that your fix works and commit the changes to your feature branch.
3. You may have noticed that the "Bed" column in the table now shows any beds as an array (`[ ... ]`, or `[]`).  This is because that is how the `fetchPlantAssets` function returns them. Modify the code in the `App.vue` so that the beds are again shown as a comma delimited list.
   - Hints: 
     - You only need to change the template.
     - JavaScript has an Array method that will turn an array into a a comma delimited string.
4. Confirm that your fix works and commit the changes to your feature branch.
5. (More Challenging) Unless you already fixed it, when the quantity is created for our harvest log it will always use `weight` as the `measure`.  But not all units are `weight`.  There are other measures such as `Count`, `Rate`, `Ratio`, `Length/depth` and others. Modify the code in the `App.vue` file so that the `measure` of the quantity is set according to the unit that is selected.
   - Hints:
     - Go to the "Setup" -> "Taxonomy" pages find the "Unit" taxonomy and and click on the button to "List terms". You'll notice that all of the units (e.g. "POUND", "HEAD", "EACH") have a parent term.  The parent terms indicated the "measure" for the unit.
     - Given a unit, its `relationships.parent[0].id` gives the `id` of the parent unit object, which will contain the name of the measure.
     - There is a function in the `farmosUtil` library that returns a `Map` object that allows you to get a unit object given its `id`.
   - Note: Currently all of the units have a parent unit that gives its measure. But someone using farmOS someone could easily create a new unit that does not have a parent.  If a unit does not have a parent, you should set the measure to `''`.
6. Confirm that your fix works and commit the changes to your feature branch.

## Optional Challenge - Improved User Efficiency

1. A number of the crops have only one possible harvest unit.  When that is the case it seems wasteful to make the user pick it from the "Unit" select. Modify the code in `App.vue` so that the user does not need to select the unit if there is only one harvest unit for the selected crop.
   - Tip: There are a number of reasonable ways to do this!
2. Confirm that your fix works and commit the changes to your feature branch.

## Checklist

- Plants are fetched using the `getPlantAssets` function instead of using `fetch` directly.
- The "Unit" select is populated for the selected crop using the `getHarvestUnits` function.
  - The initial value of the `unitList` is an empty array.
- Clicking submit with a completed Harvest form creates a harvest log with the form data.
- Optional Bug Fixes
  - Beds are listed as a comma delimited list.
  - Only plants that can be harvested (i.e. are in the ground) are listed in the table.
  - The quantity in the harvest log has the correct `measure` based on the selected unit.
- Optional User Efficiency Improvement
  - User is not forced to select a unit for the harvest if there is only one possible harvest unit for the selected crop.

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