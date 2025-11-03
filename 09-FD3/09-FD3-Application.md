# 09 - FD3 - Application

In this assignment you will replace some additional components in the Harvest form with components from FarmData2.

## Preliminaries

1. Restart your FarmData2 Development Environment.
2. Synchronize your `development` branch with the upstream to add the starter code for this assignment to your repository.
3. Rebuild the documentation:
   ```
   npm run docs:gen
   ```
4. Use the "FD2 School" menu to navigate to the "FD3-Application" page.
   - This page will contain a working solution to the FD2 Activity assignment, which is also the starter code for this assignment.
5. Create a new feature branch from `development` and switch to it for your work on this assignment.
6. Open the FarmData2 folder in VSCodium.
7. Find the `modules/farm_fd2_school/src/entrypoints/FD3_Application/App.vue` file and open it.
   - You will modify the code in the `App.vue` file to complete this assignment.
7. Start the documentation server as referencing the documentation for the components you will be using will be helpful.

## A Note

You will find it very helpful to consult the documentation for the components that you are using.  Each component's documentation has a "Live Example" that you can play with to understand its props and events. Each component's documentation also has a "Usage Example" that you can adapt for use in the Harvest form.

Note however, that many of the components that you will be using in this assignment have props and events that we have not discussed or for which the importance will not be clear at this point. They have a purpose in full FarmData2 forms, but are not particularly important to our learning at this point. Thus, those props and events should be omitted when using the components in your Harvest form.  For example, it is not necessary to handle the `ready` or `valid` events for this assignment. 

## The `CommentBox` Component

1. Replace the HTML `textarea` used for the "Comment" input in the Harvest form with a FarmData2 `CommentBox` component.
2. Rebuild the `school` module, reload the page.
3. Confirm that the new "Comment" input works.
4. Commit the changes to your feature branch.

## The `SubmitResetButtons` Component

1. Replace the HTML buttons used for "Submit" and "Reset" in the Harvest form with a FarmData2 `SubmitResetButtons` component.
2. Rebuild the `school` module, reload the page.
3. Confirm that the new "Submit" and "Reset" buttons work.
4. Commit the changes to your feature branch.

## The `NumericInput` Component

1. Replace the HTML `text` input used for the "Quantity" input in the Harvest form with a FarmData2 `NumericInput` component.
   - The component should have small and medium increments/decrements of 1 and 5.
2. Rebuild the `school` module, reload the page.
3. Confirm that the new "Quantity" input works.
4. Commit the changes to your feature branch.

## The `CropSelector` Component

1. Change the HTML `select` that is used for selecting the "Crop" in the Harvest form to be a FarmData2 `CropSelector` component.
   - Note: There will be some additional challenges with making this change.
     - The Harvest form is currently built on the assumption that the `crop` property in the Vue `data` contains an object representing the crop.
       - E.g. `{ id: 1, attributes: { name: 'ARUGULA' } },` 
     - However, checking the documentation for the `CropSelector` shows that the payload for the `update:selected` event is a string containing just the name of the crop (e.g. `"ARUGULA"`).
     - Corresponding changes will need to be made throughout the Harvest form to use `crop` as the name of the crop, rather than as an object.
2. Rebuild the `school` module, reload the page.
3. Confirm that the new crop selector works.
4. Commit the changes to your feature branch.

## Checklist

- The "Crop" `select` has been replaced with a `CropSelector` component.
- The "Quantity" `text` input has been replaced with a `NumericInput` component.
- The "Comment" `textarea` has been replaced with a `CommentBox` input.
- The "Submit" and "Reset" buttons have been replaced with a `SubmitResetButtons` component.
- Unused code in the `<script>` and `<style>` elements has been removed.
- Submitting a correctly completed form creates a valid harvest log.

## Turning In Your Work

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your origin repo.
3. Go to your origin repo on GitHub.
4. Make a PR to the `development` branch in the upstream repository.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR to ensure that you have only made changes in the `modules/farm_fd2_school/src/entrypoints/FD3` directory. Make any necessary changes, commit them to your feature branch and push it again to update the PR.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)