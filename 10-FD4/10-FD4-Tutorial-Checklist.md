## Grading Checklist


- The following `data-cy` attributes have been added to the `<template>`
  - [x] - `app-heading`: "Shopping List Application" `<h1>` 
  - [x] - `add-item-button`: "Add Item" `<button>`
  - [x] - `cancel button`: "Cancel" `<button>`
  - [x] - `new-item-input`: "New Item" text `<input>`
  - [x] - `high-priority-checkbox`: "High Priority" checkbox `<input>`
  - [x] - `save-item-button`: "Save Item" `<button>`
  - [x] - `nice-job-message`: "Nice Job!" `<p>`
- The "Check the page state when loaded" test asserts that:
  - [x] - `app-heading` has correct text.
  - [x] - `add-item-button` is visible.
  - [x] - `nice-job-message` is visible and has correct text.
  - [x] - `cancel button` does not exist.
  - [x] - `new-item-input` does not exist.
  - [x] - `high-priority-checkbox` does not exist.
  - [x] - `save-item-button` does not exist.
- The "Add Item button shows full form" test:
  - [x] - clicks on the "Add Item" button.
  - asserts that
    - [x] - `cancel-button` is visible.
    - [x] - `new-item-input` is visible.
    - [x] - `high-priority-checkbox` is visible.
    - [x] - `save-item-button` is visible and is not enabled.
    - [x] - `add-item-button` does not exist.

## Common Feedback
