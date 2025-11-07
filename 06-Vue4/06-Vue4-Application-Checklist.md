- Computed properties are used to:
  - Disable "Submit" button any time the form data is not valid.
    - [x] - "Submit" button's `disabled` property in bound to computed property.
    - [x] - Computed property correctly returns `true` when all data is valid and `false` when it is not.
  - Sort plants in the table from oldest to newest in the table.
    - [x] - `v-for` the `<tr>` element is bound to computed property.
    - [x] - Computed property sorts objects by date from oldest to newest.
- [x] - Work is spread across multiple commits.

Common Feedback:
- I think that the name of this computed property could be more descriptive of what it does. Maybe `isFormValid` or `submitButtonDisabled` or something similar?
- I think that the name of this computed property could be more descriptive of what it does. Maybe `sortedPlants` or `sortedPlantList`?
- This `if` statement can be simplified. Notice that if the condition is `true` you return `true`, else you return `false`.  So why not just return the condition as a boolean?
- There are a few more conditions to be checked here.  To ensure that the form has been fully completed you need to check that:
- [x] - the date is set to a valid value.
- [x] - A crop is selected.
- [x] - A plant is selected.
- [x] - A quantity is entered.
- [x] - A unit is selected.

