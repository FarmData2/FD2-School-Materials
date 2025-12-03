## Grading Checklist

- [x] - Tests use `get` and `find` appropriately.
- Test for the Initial State of the Harvest form:
  - [x] - Checks visibility and values for:
    - Header, "Date", "Crop", "Submit/Reset" buttons.
  - [x] - Checks "Submit" button is disabled.
  - [x] - Checks non-existence of:
    - "Plant" table, "Quantity", "Units", "Comment".
- Test for Selecting a Crop with Harvestable Plants:
  - [x] - Selects a crop with harvestable plants.
  - [x] - Checks visibility and values for:
    - "Plant" table, "Quantity", "Units", "Comment".
- Test for Selecting a Crop without Harvestable Plants:
  - [x] - Selects a crop without harvestable plants.
  - [x] - Checks visibility and content of "no plants" message.
  - [x] - Checks non-existence of:
    - "Plant" table, "Quantity", "Units", "Comment".
- [x] - Work is spread across multiple commits.

## Common Feedback

-Overall a good solution. It would be preferable from the perspective of readability and consistency to use the `data-cy` values for the elements you are trying to `find` within the components.

- It would be better to use the `data-cy` value in the `find` to get the element inside of this component.  See the documentation for the component to find the `data-cy` values that it contains.