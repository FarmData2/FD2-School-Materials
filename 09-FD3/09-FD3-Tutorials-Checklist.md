## Grading Checklist

- The `DateInput` component is defined in `components/DateInput/DateInput.vue`.
  - In the `<template>`:
    - [x] - creates the label and date input.
    - [x] - date input is bound using `v-model` to the `pickedDate` property in the Vue `data`.
  - In the `<script>`:
    - Component, props and events are declared:
      - [x] - the `name` is `DateInput`.
      - [x] - `initDate` prop is declared in `props`.
      - [x] - `date-change` event is declared in `emits`.
    - [x] - `pickedDate` property is initialized to `initDate`.
    - Component correctly emits `date-changed` event:
      - [x] - `watch` on `pickedDate` emits `date-changed` event.
      - [x] - `date-changed` event has the new date as its payload.
- The `App.vue` for the Harvest form:
  - In the `<template>`:
    - [x] - does not directly use the date input HTML element.
    - [x] - includes a `DateInput` element with:
      - [x] - `date` property `v-bound` to the `initDate` prop.
      - [x] - `v-on:date-changed` handler updates `date` property.
  - In the `<script>`:
    - [x] - imports the `DateInput` component.
    - [x] - declares the `DateInput` component in `components`.
- [x] - Work is spread across multiple commits.

## Common Feedback

-