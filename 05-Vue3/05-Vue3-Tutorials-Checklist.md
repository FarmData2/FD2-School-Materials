- [x] - The "Add Item" and "Cancel" buttons show and hide the form for adding a new item.
  - [x] - The "AddItem" and "Cancel" buttons call the `doEdit` method correctly.
- [x] - The `add-item-form` `div` is shown when `editing`.
- [x] - The `v-on` handlers for the `text` input and `button` call the `saveItem` method.
- [x] - The "Nice job! You've bought all your items!" message appears when the list is empty and is hidden when an item is added.
- [x] - The `items` list is initially empty.
- [x] - The `saveItem` method is added to the Vue `methods`.
  - [x] - The `saveItem` method has been extended to clear the `text` input when a new item is saved.
- [x] - The `doEdit` method has been added to the Vue `methods`
  - [x] - The text field is cleared if `doEdit` is clicked.
- [x] - Work is spread across multiple commits.

## Common Feedback

- The `v-on` here should call the `saveItem` method. This will remove the duplicate code, which can be a source of maintenance errors.