
- FD2 uses `v-bind` instead of `:` shorthand.
  - less overhead for beginners.
  - also uses `v-on` instead of `@` for the same reason.

- Javascript spread operator 
  - Shortcut for making a copy of an array.
    - Other ways...
      - `copy = [...arr]`
      - `copy = Array.from(arr)`
      - `copy = arr.slice()`
      - `copy = [].concat(arr)`
    - Just one of the things that I don't like about Javascript...

- Javascript's array sort and sorting objects
  - Making a sort comparator.
  - Show a simple example... or show an ask AI?

  - Reference for Javascript Array class methods?
    - Lots of them... 
    - If you have to do something that seems common...
      - Look at the reference
      - Ask your favorite AI.

- Computed properties automatically recompute when any data that they use changes.
- Computed properties are only for transforming existing data into a new representation of that data.
  - E.g. the reversed list of items in the tutorial.
- Computed properties must:
  - not change data (huge source of bugs!!!)
  - return a value
- Computed properties can be used anywhere a data property is used with the exception that they cannot be changed.

- Show computed property in the tutorial using the Vue Devtools!
  - Show added items are added to items and the computed property.
  - They do it in the tutorial... but you know.

- Methods vs Computed Properties
  - Methods called explicitly on an event or from another method
    - can change data
  - Computed properties called implicitly when any data that it uses changes.
    - cannot change data
    - But can be used in template so presentation changes when computed property changes. 
    - They generate new or transformed information from existing data.
      - Sorted list, complex boolean condition, etc.

Make this a question for them?
- Use the example of factoring out repeated code:
  - Earlier tutorial did it with the code to add an item.
    - this modified the data `item` by pushing to it.
    - so that was a `method`
  - Now we might have repeated code to disable both the "Save" button and the "High Priority" checkbox.
    - This could be a method... but then it wouldn't be recomputed automatically.
    - This can be a computed property because it doesn't change any `data`
    - It just computes a new value from the existing `data`.

- Naming computed properties
  - state what it is not what it does.
  - reversedItems
  - newItemValid (implies true/false)

- Vue Reactivity as a concept...
  - Computed properties recompute
  - Updates to {{ }} content

- Why is the computed property nice?
  - Can just change the data and know the view is going to be right.

- Mention JS logical, relational and arithmetic operators are largely the same as what they are in Java/C/C++
  - `&&`, `||`, `!`
  - `>`, `>=`, `<`, `<=`, `!=`, `==`, `===`
  - `+`, `-`, `*`, `/`, `%`


  - I think watches are too much to throw in here...
  - And `watches` run????
    - Can we include `watch` here as well?
      - Lots of tutorial pages discuss when to `watch` vs when to use `computed` property... so maybe it makes good sense to add it here?
      - Use `watch` for `crop` change to update `plantList` with if/else?
    - Watch can change data...


---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)