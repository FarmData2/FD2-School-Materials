# 02 - Vue1 - Class Notes

**DRAFT**

- script in `<script>`
- don't need to import the CDN, done by the build.
```
<script>
export default {
  data() {
    return {};
  },
};
</script>
```

- review `v-model` 
  - show binding a field to data value
  - need to refresh in Vue devtools to see changes made in UI.

- review `v-bind`
  - we use of `v-bind` instead of `:` shortcut for key.

- Cover JS object syntax:
  ```
    items: [
      {id: 1, label: '10 party hats'},
      {id: 2, label: '2 board games'},
      {id: 3, label: '20 cups'},
    ],
  ```
  - note trailing commas.
    - want's them when object or array is split across multiple lines
    - Prevents you from forgetting to add them later when you add more items to an object or an array.

  - use of "" vs '' in HTML (template) vs JS/Vue (script)

