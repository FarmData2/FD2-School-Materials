# 10 - FD4 - In Class Hands-On Activities

## Preliminaries

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize the `development` branch in your clone with the upstream `development` branch.
   - After you synchronize tje starter code for this activity will have been added to `development` in the directory `modules/farm_fd2_school/10-FD4-Activity-Starter`.
   - This is also the solution to the tutorials.
3. Create and switch to a new feature branch for your work on these activities.
4. Open the `index.html` and `firstTest.e2e.cy.js` files from the `modules/farm_fd2_school/10-FD4-Activity-Starter` directory in VSCodium.
5. Open the same `index.html` file in the browser.

## Testing the Save Item Feature

Create an E2E test in `firstTest.e2e.cy.js` for the process of saving a new item to the list.

Follow the incremental process you saw in the tutorial for building tests.

1. Walk through the process of adding a new item to the list manually.
   - Start from a freshly loaded page as that is where the test will start.
   - Note the actions and assertions that will be needed in the test.
     - You'll need at least 3 actions, and at least 3 assertions.
2. Create basic failing test.
3. Write actions and assertions one-by-one, running the test between each to ensure that they work.
   - Hints:
     - Use the [Cypress Reference](../CypressReference.md) and/or your favorite AI as needed to help with creating the actions and assertions.
     - Add a `data-cy` attribute to the `<ul>` element or to each `<li>` element.
       - If adding `data-cy` attributes to the `<li>` elements, use an `index` with the `v-for` so that each `<li>` can have a unique `data-cy` value.

## Optional Extra: Test the Cancel Feature

When the user clicks the "Add Item" button the full form for adding an item appears. This includes the "Cancel" button. When the user clicks this "Cancel" button the application returns to its initial state. Create a new Cypress test in `firstTest.e2e.cy.js` that verifies this functionality.

## Optional Extra: Test Item Name Length Feature

When the user is entering the name of a new item to be added to the list, the "Save Item" button is disabled until the item mane has more than 5 characters. Create a new Cypress test in `firstTest.e2e.cy.js` that verifies this functionality.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)
