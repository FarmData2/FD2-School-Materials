# 06 - Vue4 - Class Notes

## Instructor ToDo Before Class

- Merge 
  - `06-Vue4-Tutorial-Soln`
  - `06-Vue4-Activity-Soln`
  - `06-Vue4-Application-Starter`
  - `07-FD1-Tutorials-Starter`

## Questions
  
Take questions and show solutions as is helpful for providing answers.

- 05-Vue3-Application - Methods and Conditional Rendering
  - Solution is in the `06-Vue4-Application-Starter` branch
    - added `resetForm` method.
    - no crop or unit selected by default.
      - `crop = '',`
      - `unit = '',`
    - hide form when no crop is selected.
      - `v-if="crop != ''"`
- 06-Vue4-Tutorials - Attribute Binding and Computed Properties
  - Solution is in the `06-Vue4-Tutorials-Solution` branch
  - Disable "Save" button if item is too short.
    - `v-bind:disabled="newItem.length < 5"`
  - Display the items with newest items at the top.
    - `reversedItems` computed property returns a reversed copy of the `items` array:
      ```
      reversedItems() {
        return [...this.items].reverse();
      }
      ``` 
      - Let's pick apart how this works a little:
        - The _array spread_ operator.
          - Used here as a shortcut for making a copy of an array.
            - `[...[1,2,3]]` -> `[1,2,3]`
          - More generally the spread operator breaks and array apart (i.e. spreads it) and replaces it with its individual elements.
            - `['a',...['p','q'],'z']` -> ['a','p','q','z']
        - Reversing the array.
          - `.reverse()`
            - Like Java/Python and many other languages there are lots of methods that operate on arrays.
              - If you think what you need to do is something common that many other people will want to do, look it up in the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) or ask your favorite AI:
                - Reversing
                - Extracting a sub-array
                - Removing elements
                - Sorting
                - ...
    - Uses `reversedItems` to render the list instead of `items`
      - `v-for="item in reversedItems"`
        - Changed from `v-for="item in items"`

## Computed Properties and Reactivity

- Computed Properties are used a lot like Vue `data` properties.
  - `v-for="item in reversedItems"`
  - `this.reversedItems.length`
  - But because a computed property is a function that returns a value we can't assign to it like we can a `data` property.
    - `this.reversedItems = []` will not work.
- Computed properties automatically recompute anytime that any of the `data` that they use changes. For example:
  - The `reversedItems` computed property uses `this.items`.
  - So any time `this.items` is changed, `reversedItems` will be recomputed.
  - Demo this:
    - Use `06-Vue4-Tutorials-Solution/index.html`
    - Open Vue Devtools
    - Show `items` and `reversedItems` are `Array[0]`
    - Add new item to the list.
      - Show `items` contains the new item.
        - Because our event handler put it into `this.items`.
      - Show `reversedItems` has that item also.
        - Because it is a computed property that uses `this.items`.
        - So it was automatically recomputed when `this.items` was changed by the event handler.
    - Add another new item to the list.
      - Show it is at the end of the `items` Array (index `1`).
      - Show that it is at the start of the `reversedItems` Array (index `0`).
      - Again happened automatically because `reversedItems` is a computed property that uses `this.items` and `this.items` was changed.
    - Also note that the list rendered in the page changed.
      - This is because that list was rendered using the `reversedItems` computed property, which changed because `list.items` changed, which changed because the event handler added the new item.
    - This is Vue's _Reactivity_ at work!
      - When we modify data, Vue reacts by updating all of the things that depend upon the changed data.
- Computed properties:
  - Must return a value.
  - Must not change any `data` properties.
    - Careful with this... its a major source of bugs.
    - Can create infinite loops.
      - For example, if `reversedItems` actually reversed `items` then when it did so, it would be recomputed again because `items` changed. That would then change `items` which would cause it to recompute again...
      - That one is pretty obvious, but this loop could ripple through many different computed properties and methods.
        - For example, computed property `A` might use `data` property `X`, and computed property `B` might use computed property `A` and also calls method `C`. Now if method `C` changes `X` we can get a similar infinite loop.
    - The linter in FarmData2 helps with this.
      - Catches simple cases where a computed property directly changes a `data` property.
        - Will be underlined in red.
        - Will have the message "Unexpected side effect in ..."
        - The `pre-commit` hook will prevent you from committing. 
      - Won't catch more complex instances (e.g. calls to methods that change a `data` property).
  
### Computed Properties vs Methods

- Use a computed property when you want to:
  - Reconfigure existing data for display.
    - `reversedList`
    - A sorted list.
  - Compute a new value from existing data.
    - `formValid`
    - `total`, `minimum`, `maximum`
  - Avoid storing redundant data that will need to be updated in multiple places.
  - Have the value update automatically when the associated `data` properties change.
- Use a method when you want to:
  - Modify `data` properties in the Vue instance.
    - Add an item to the list.
    - Empty the list.
  - Execute the code on an event.
    - `v-on:click`
  - Explicitly call the method from another method.
    - `this.resetForm()` 

Some examples from the tutorials.
- We factored out the code that adds a new item to the `items` list.
  - This required:
    - Modifying the `items` property by pushing to it.
    - Needed to be called on an event.
    - So this had to be a `method`
- In the the hands on activity you will disable both the "Save" button and the "High Priority" checkbox.
  - This computation:
    - Is is a new value computed using existing data.
      - `this.newItem.length > 5`
    - It does not change any `data` properties.
    - We want it to update automatically (i.e. reactively) when the associated `data` properties change.
    - So this should be a `computed` property.

## Naming Conventions

Common naming conventions keep things consistent across large code bases. It is common to:

- Name `data` properties with nouns because they represent things.
  - `date`, `cropList`, ...
- Name computed properties with:
  - Nouns when they represent things.
    - `reversedList`
  - Questions when they give the answer to a question.
    - `newItemValid`, `formValid`
      - Often but not always `boolean`
- Name `methods` with verbs because they do things.
  - `resetForm`

## Some Additional Commentary on JavaScript 

### `v-bind` vs `:`

Code in FarmData2 uses `v-bind` instead of the `:` shorthand.
  - This results in less cognitive overhead for beginners.
  - Similar to how it uses `v-on` instead of `@`.
  - The Prettier plugin is configured to convert `:` to `v-on`.
    - So you can write with `:` if you like.
    - But when you commit the `pre-commit` hook will change `:` to `v-on`

### Relational and Arithmetic Operators

The logical, relational and arithmetic operators in JavaScript are largely the same as what they are in Java/C/C++ and many other languages.

- `&&`, `||`, `!`
- `>`, `>=`, `<`, `<=`, `!=`, `==`, `===`
- `+`, `-`, `*`, `/`, `%`

The `===` is unique to JavaScript as we discussed previously.

### _Truthiness_ in JavaScript

Because JavaScript is not _statically typed_ a variable can contain different values at different times.  Thus a a boolean expression like in `if (x && y)` might be performing the logical AND of two boolean values, an integer and an array, an object and a boolean, or any other combination. To deal with these scenarios JavaScript will convert all values in a boolean expression to be either _`truthy`_ or _`falsy`_.  Values that are `truthy` evaluate as `true` and values that are `falsy` evaluate as false.

The `falsy` values include:
- `false`, `0`, `''`, `""`, `null`, `undefined`, and `NaN`.
The `truthy` values are everything else.
- `true`, non-zero numbers, non-empty strings, Arrays, and Objects.
  - Note: Arrays and Objects are `truthy`. even if they are empty (`[]` or `{}`).

Some examples may help to clarify:
- `0 && true` -> `falsy && truthy` -> `false`
- `{} || 0` -> `truthy || falsy` -> `true`

## Hands On Time

Spend the the rest of the time working on 06-Vue4-Hands-On activities.
- But save a few minutes for wrap up.

## Wrapping Up

Here's a preview of what you'll be doing in the application and the next tutorials.

### 06-Vue4-Application

You'll used what you've learned about attribute binding and computed properties to add some nice features for the user.

- Demo from the `07-FD1-Application-Starter` branch
  - `git switch 07-FD1-Application-Starter`
  - `npm run build:school`
  - `Shift+reload`
  - Open "FD2 School" -> "FD1"
    - Show that the "Submit" button is disabled unless the form is valid.
    - Show that the table of plant is sorted from oldest to newest.
      - Most likely to want to harvest from the oldest plants, so sorting this way makes things easier for the user.

### 07-FD1-Tutorials

- This tutorial: 
  - Introduces Application Programming Interfaces (APIs).
  - Shows how to use an API to fetch data from a server.
  - Is not in Vue School.
  - Is text based instead of following a video.
    - So may take a little longer.
    - Plan accordingly.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)