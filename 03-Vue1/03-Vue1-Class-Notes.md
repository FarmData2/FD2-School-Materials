# 03 - Vue1 - Class Notes

**DRAFT**

## Instructor ToDo Before Class

- Merge...

## Stuff 

- Big picture...
  - What they've built so far.
  - What they are doing next.

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
  - we use of `v-bind` instead of `:` shortcut for `key` in `v-for`.

- Cover JS object syntax shown in tutorial...
  ```
    items: [
      {id: 1, label: '10 party hats'},
      {id: 2, label: '2 board games'},
      {id: 3, label: '20 cups'},
    ],
  ```
  - nothing special about `id` its just a name and a unique identifier.
  - note trailing commas.
    - want's them when object or array is split across multiple lines
    - Prevents you from forgetting to add them later when you add more items to an object or an array.

  - Might have noticed that commit also auto formats if you didn't!

  - use of "" vs '' in HTML (template) vs JS/Vue (script)
    - nesting of "'...'" and '"..."'

- Show Vue Devtools.
  - Show refresh button
  - Close and reopen Devtools if Vue content doesn't show.

- Show rebuild
  - Show SHIFT+reload in browser to see changes.
  - Note the `num run watch:school` command here.
    - Especially if it didn't come up in class two


## Instructor ToDo After Class

- Merge blah blah.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)