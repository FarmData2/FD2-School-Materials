- The inputs are bound to Vue `data`:
  - [x] - "Date"
  - [x] - "Crop"
  - [x] - "Plant" radio buttons
    - [x] - The value of each radio button will be index in the array/table.
  - [x] - "Quantity"
  - [x] - "Units"
  - [x] - "Comment Box"
- The initial values for inputs are set correctly in the Vue `data`:
  - [x] - The "Date" is June 15, 2019.
  - [x] - The "Crop" is "RADISH".
  - [x] - The "Plant" is -1 (or null).
  - [x] - The "Quantity" is 1.
  - [x] - The "Units" is "BUNCH".
  - [x] - The "Comment Box" is empty.
- [x] - Clicking the "Submit" button displays the "Submit was clicked." message in the Devtools console.
- [x] - Clicking the "Reset" button displays the "Reset was clicked." message in the Devtools console.
- [x] - Work is spread across multiple commits.

## Common Feedback

- This solution assumes that the plants will always appear in the array in order by `plant.id` and that they have `id`s 1,2,3...  A more robust solution would be to use an `index` in the `v-for` and use that as the `value` for each radio button.  E.g. `v-for="(plant,index) in plantList"`
- Using `''` for the initially selected radio button works. But it may be more consistent to use `-1`, which is a common convention for values that are invalid indices (e.g. many searching algorithms will return `-1` when the value being searched for is not found).
- The property name `value` here is not very descriptive. Maybe use something like `quantity`, which will make it more clear what the value is when the property is used at other places in the code.