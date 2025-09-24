
Bunch of stuff here about modifying the plant list... we may not need this if we just wait until we fetch the plants from farmOS.

  - JavaScript if/else and `===` vs `==` vs `=`
  - Introduce `watch` by watching `items` in the shopping list.
  - Using `watch` vs `v-on:change` for selections
    - best to use `v-model` and `watch` the Vue `data` property.
    - Its the "Vue way!"

## Clearing the Default Plants

The table on the harvest form is intended to show just the plants of the type of crop that the user selected for harvest. So, since we now don't have a crop selected when the Harvest page loads, we also shouldn't show any plants in the table when the page loads.

1. Comment out the objects in the `plantList` array so that `plantList` is initially assigned to an empty array. Be sure to comment the objects out rather than deleting them because you'll need them later.
   - Hint: You did this with the shopping list `items` in the tutorials.
   - Hint: There is a [Shortcut Key](../FD2CommandReference.md) for commenting out lines in VSCodium.
2. Rebuild the school module and reload the page to ensure that the table is empty when the page is loaded.
3. Commit the changes to your feature branch with a meaningful commit message.

## Reacting to Changes in the Selected Crop

Now, when the user changes the selected crop we want to populate the table with the plants of that crop type that are available to be harvested. To do that we'll need to detect when the selected crop changes and run some code In Vue, a `watch` allows us to run code when the value of a Vue property changes.

1. Add the `watch` property shown below to your Vue instance between the `data` and `methods` sections as shown:
   ```
   data: () {
      ...
   },
   watch: {
      crop() {
         console.log("Crop changed to " + this.crop);
      }
   },
   methods: {
      ...
   },
   ```
2. Rebuild the school module and reload the page.
3. Open the Console tab in the Devtools.
4. Change the "Crop" selection and ensure that the expected message appears in the console.

### Showing the RADISH Plants

For now, let's change the code so that anytime a crop is selected our four "RADISH" plants appear in the table. This isn't quite correct, but it moves us in the right direction. Later there will be an optional section that improves this a little bit, and then in a later topic we'll actually fetch and display the live data for the correct plants from farmOS.

5. Modify the `watch` function for the `crop` property so that instead of displaying a message in the console when a crop is selected, the four "RADISH" plants are shown in the table.
   - Hint: This will be very similar to adding a new item to the shopping list.
6. Rebuild the school module and reload the page to ensure that the "Radish" plants appear in the table when a crop is selected.
7. Commit the changes to your feature branch with a meaningful commit message.

### Only Show RADISH Plants when RADISH is Selected

8. Modify the `watch` for the `crop` so that it only displays the "RADISH" plants when "RADISH" is the selected crop. When any other crop is selected no plants should be displayed.
   - Hint: Ask your favorite AI how to write an `if/else` statement in Javascript.
   - Hint: You can remove all elements from an array by setting its `length` property to 0. E.g. `this.plantList.length = 0;`.
9. Rebuild the school module and reload the page to ensure that the "RADISH" plants only appear in the table when "RADISH" is selected.
10. Commit the changes to your feature branch with a meaningful commit message.

## Hide Unnecessary Content until there are Plants to Harvest

Currently the empty table, the quantity input and the "Unit" select all appear in the form even when there are no plants to harvest. Let's hide those elements any time there are no plants to harvest.

1. Modify the `<template>` so that the table of plants, the "Quantity" input and the "Unit" select are hidden if there are no plants available for harvest.
   - Hint: This is very similar to how you hid the shopping list if it contained no items.
2. Rebuild the school module and reload the page to ensure that the table, "Quantity" input and "Unit" select are hidden when the page is first loaded and that they appear when the "RADISH" crop is selected.
3. Commit the changes to your feature branch with a meaningful commit message.
