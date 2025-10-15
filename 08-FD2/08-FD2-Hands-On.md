# 08 - FD2 - In Class Hands-On Activities

## Preliminaries

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize the `development` branch in your clone with the upstream `development` branch.
   - After you synchronize a solution to the tutorials will have been added to `development` in the directory `modules/farm_fd2_school/src/entrypoints/08-FD2-Activity`.
   - This is also the starter code for the in class activity.
3. Create and switch to a new feature branch for your work on these activities.
4. Open the "FarmData2" -> "FD2 Activity" page in the browser.
5. Open the `modules/farm_fd2_school/src/entrypoints/08-FD2-Activity/App.vue` file in VS Codium.

## Making a Method for Submit

Currently the "Submit" button has a `v-on:click` that just uses `console.log` to display a message in the console.  To actually submit the form and create a harvest log you'll need a method.

1. Add a new method named `submitForm` to the Vue instance that is called when "Submit" is clicked.
2. For now have your `submitForm` method just use `console.log` to display a message in the console.
3. Rebuild the `school` module and reload the "FD2 Activity" page.
4. Use the Devtools to confirm that your `submitForm` method is being called when "Submit" is clicked.
5. Commit your changes to your feature branch.

## Creating a Quantity

Recall that to create a `harvest_log` object requires a quantity to represent the amount of the crop that was harvested. In this section you'll create a `standard_quantity` object that can be used when creating a `harvest_log`.

1. Start the documentation server.
   ```
   npm run docs:view
   ```
2. Find the documentation for the `farmosUtil` library.
3. Find the function for creating a standard quantity.
4. Add code to your `submitForm` method that creates a standard quantity with the following hard-coded values for testing:
   - `measure`:  `'weight'`
   - `value`: `7.5`
   - `label`: `'harvest'`
   - `units`: `POUND`
   - Omit the `inventoryAsset` and `inventoryAdjustment` parameters.
   - Notes:
     - The `createStandardQuantity` function is an `async`.
     - So make your `submitForm` method `async`.
     - Use `await` when you call `createStandardQuantity`.
5. Store the result in a `const` variable and log it to the console for testing.
6. Rebuild the `school` module and reload the "FD2-Activity" page.
7. Fill out the form and click the "Submit" button to create the quantity.
8. Check the Devtools console to confirm that the quantity was created.
9. Check "Records" -> "Quantities" in the farmOS UI to confirm that the quantity has been created.
   - Hint: You can click the "ID" column header to bring the newest quantities to the top.
   - Note: Your new quantity will not have any values for the "Log..." columns because it is not yet associated with a log.

## Putting Real Data into the Quantity

1. Change the code in your `submitForm` method so that the quantity is created using the values that you have entered in the form.
   - Hints: 
     - Use the values in the Vue `data` as parameters to the `createStandardQuantity` function.
     - The `unit` in the Vue `data` is a `unit` object so you need to access its `name` property.
     - Continue to use `weight` as the `measure` (even though it may not be accurate).
     - Continue to use `'harvest'` as the `label`.
2. Rebuild the `school` module and reload the "FD2-Activity" page.
3. Fill out the form and click the "Submit" button to create the quantity.
4. Check "Records" -> "Quantities" in the farmOS UI to confirm that the newest quantity was created with the values that you entered in the form.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)
