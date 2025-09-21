# 05 - Vue3 - In Class Hands-On Activities

## Preliminaries

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize the `development` branch in your clone with the upstream `development` branch.
   - After you synchronize a solution to the tutorials will have been added to `development` in the directory `modules/farm_fd2_school/05-Vue3-Tutorials-Soln`.
3. Create and switch to a new feature branch for your work on these activities.
   - Create this feature branch from the branch you created for the tutorials to continue from your prior work.
   - OR create this feature branch from `development` to work from the provided solution.

## Hide Form on Save
   
Currently when a new item is added to the list, the form for adding items remains visible.  But it might be preferable to have the form hidden after a new item is saved.

1. Change the code so that the form is automatically hidden after a new item is saved.
  - Hint: Make a change to the `saveItem` method.

## Populate the Shopping List

Currently the shopping list is initially empty.  However, there are some things that any good party will need.  So it might be useful to have a way to quickly add these essential items to the list.

1. Add a button to the page that when clicked will populate the shopping list with the items that were in the original tutorial:
   ```
   10 party hats
   2 board games
   20 cups
   ```
   - Hint: Add a new method that will `push` these things to the `items` array in the Vue data.

## Deleting Items (More Challenging)

1. Add button beside each item that will delete it from the list when the button is clicked.
   - Hint: Use an `index` with the `v-for` to pass the index of the item to delete to a new method that removes it from the `items` array in the Vue data.
     - Caution: Don't name the new method `delete` because that is a reserved word in JavaScript and thus cannot be used as a method name.
   - Hint: Look up or ask your favorite AI how to delete an item from an array in JavaScript.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)