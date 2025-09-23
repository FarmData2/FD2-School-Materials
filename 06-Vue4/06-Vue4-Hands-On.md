# 06 - Vue4 - In Class Hands-On Activities

## Preliminaries

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize the `development` branch in your clone with the upstream `development` branch.
   - After you synchronize a solution to the tutorials will have been added to `development` in the directory `modules/farm_fd2_school/06-Vue4-Tutorials-Soln`.
3. Create and switch to a new feature branch for your work on these activities.
   - Create this feature branch from the branch you created for the tutorials to continue from your prior work.
   - OR create this feature branch from `development` to work from the provided solution.

## Disable the High Priority Checkbox

In the "HTML Attribute Binding in Vue 3" tutorial you used `v-bind` to disable the "Save" button when the input contained less than 5 characters.

1. Disable the "High Priority" checkbox under the same condition that the "Save" button is disabled.

## Factoring Out Repeated Code using a Computed Property

Here after disabling the "High Priority" checkbox above your page contains the same code in multiple places. Factoring that code out into a new computed property can prevent future bugs.

1. Define a new computed property named `newItemValid` that returns `false` if the input contains less than 5 characters and `true` if it contains 5 or more characters.
2. Use the Vue Devtools to check that the `newItemValid` computed property is working properly.
3. Change the `v-bind` that disables the "Save" button to use the `newItemValid` computed property instead of an explicit condition.
4. Use the `newItemValid` computed property to also disable the "High Priority" checkbox.
5. Test the page to ensure that both the "Save" button and the "High Priority" checkbox are enabled and disabled as appropriate.

## Display `items` in Sorted Order

1. Add a new computed property `sortedItems` that returns a new array with the `items` sorted by the number of the items that are needed. For example, "2 board games" would come before "10 party hats", which would come before "20 cups".
   - Hint: Try asking your favorite AI "How can I sort an array of objects with this format { id: 1, label: '10 party hats' } in JavaScript."
   - Hint 2: Remember, computed properties must not change the Vue `data`. So be sure to use the "spread operator" to copy the `items` array as was done in the `reverseItems` property.
2. Use the Vue Devtools to check that your `sortedItems` computed property is working correctly.
3. Change the page so that the items in the shopping list are now displayed in sorted order.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)