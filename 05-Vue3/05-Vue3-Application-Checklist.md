- When the page is reloaded:
  - [x] - No "Crop" is selected.
  - [x] - The table, quantity, units and comment are hidden.
- Selecting a "Crop" reveals the:
  - [x] - "Plants" table with no row selected.
  - [x] - "Quantity" input with value 1.
  - [x] - "Unit" select with no unit selected.
  - [x] - "Comment" box with the placeholder text.
- Clicking "Reset":
  - [x] - Sets the "Date" to June 15, 2019.
  - [x] - Clears any selected "Crop".
  - [x] - Clears any selected row in the "Plants" table.
  - [x] - Sets the "Quantity" to 1.
  - [x] - Clears any selected "Unit".
  - [x] - Clears any entered "Comment"
  - [x] - Hides the "Plants" table, "Quantity" input, "Unit" select and "Comment" box.
- [x] - Work is spread across multiple commits.

## Common Feedback:

- The `v-if` to hide the table can use the value of the `crop` property directly. For example: `v-if="crop != ''"`.  So it is not necessary to introduce another variable or another method as they did in the tutorial.
- Adding a `<div>` that surrounds all of the elements to be hidden and applying the `v-if` to the `div` will result in more maintainable code.
- The method for resetting the form should also reset `this.pickedPlant`. That will ensure that no plant is selected when a new crop is selected and the table is shown again.
- Be sure to create your feature branches from the `development` branch so that only the changes related to the intended assignment appear in the PR.
