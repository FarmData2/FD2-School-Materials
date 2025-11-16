## Grading Checklist

- [x] - Submitting a correctly completed form creates a valid harvest log.
- [x] - The "Crop" `select` has been fully replaced with a `CropSelector` component.
  - [x] - Changes are made to adapt to the fact that `CropSelector` emits the crop name instead of a crop object as had been used previously (i.e. `this.crop.attributes.name` has been replaced by `this.crop` in appropriate locations).
- [x] - The "Quantity" `text` input has been fully replaced with a `NumericInput` component.
- [x] - The "Comment" `textarea` has been fully replaced with a `CommentBox` input.
- [x] - The "Submit" and "Reset" buttons have been fully replaced with a `SubmitResetButtons` component.
- [x] - Unused code in the `<script>` and unused `<style>` rules have been removed.
- [x] - Work is spread across multiple commits.

## Common Feedback

- Since you do not use `validity.showStyling` or `validity.crop` in any significant way in the `script` they could have been omitted here. However, if you wanted to use them the value of `validity.crop` could have been used in the `formValid` computed property and that property could have set `validity.showStyling`. That way the component itself gets to determine if the value is valid or not.
- You are not using `createdCount` in any important way.  It is in the example code because full FarmData2 pages will use it. But it is not something you are using, so this could be omitted to simplify your code.
- You are calling the methods `submit` and `reset` here when the corresponding buttons are being clicked.  However, the methods defined below that you should be calling are `submitForm` and `resetForm`. 

- The CropSelector returns the crop name, so the crop property is no longer an object (it now just contains the name) so this will not display the name of the selected crop.

- The `data.cropList` property should be removed because it is no longer used because the list of crops is now internal to the `CropSelector` component.
- The `created` lifecycle hook is no longer needed because the `CropSelector` component now contains the code that fetches the list of crops.
- The `#harvest-date`, `#harvest-comment`, `#harvest-submit`, `#harvest-reset` styling rules can be removed because the corresponding components now hand their styling.
