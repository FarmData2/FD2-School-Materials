# 09 - FD3 - Class Notes

## Instructor ToDo Before Class

- Merge 
  - `09-FD3-Activity-Starter`
  - `09-FD3-Application-Starter`
  - `10-FD4-Tutorials-Starter`
- Do not merge:
  - `09-FD3-Tutorials-Solution`
    - This is used for in class live coding of how to modify the `DateInput` component to use `v-on` by emitting the `update:date` event.
    - The end result of this live coding is already in the `09-FD3-Activity-Starter`

## Questions

Take questions on the Application and Tutorial that are coming in.
- Application 08-FD2
  - Solution is in `modules/farm_fd2_school/src/endpoints/FD3-Tutorial`
    - Fetching of data converted to use `farmosUtil` functions.
      - `getPlantAssets` and `getHarvestUnits`.
    - Clicking submit uses `createHarvestLog` to create a harvest log.
- Tutorials 09-FD3
  - Defer questions as we will be working through a change before the Activity.

## Improving the `DateInput` Component

We'll make one particular improvement to the `DateInput` now so that it works a little more like the actual components in FarmData2. We'll start from the solution to the Tutorials to make this change.

### Look at `DateInput` Component 

- Switch to the `09-FD3-Tutorials-Solution` branch.
- Open `components/DateInput/DateInput.vue`
- `DateInput`
  - A pretty minimal component intended to illustrate how components work.
  - Provides a basic understanding of what Components are to help us when we use more complex components provided by FarmData2.
- Why use components:
  - Encapsulation - factors out repeated code.
    - Many components are much more complicated than this one.
  - UI Consistency - ensures that the "Date" input would look and act the same through the application.
- Notice:
  - `props: ['initDate']` 
    - Declares `initDate` as an input to the `DateInput` component from the page that uses it. 
  - `emits: ['date-changed']`
    - Declares `date-changed` as an event emitted from the `DateChange` component to send a change in the date back to the page that uses it.
  - `pickedDate: this.initDate` 
    - Initializes the `pickedDate` property in the Vue `data` to whatever value is provided for `initDate` by the page using the `DateInput`.
  - `this.$emit('date-changed', this.pickedDate);`
    - In a `watch` on `pickedDate`.
    - If `pickedDate` changes the `DateInput` component will emit a `date-changed` event to notify the page using the `DateInput` that the date changed.
      - `this.pickedDate` is called the _event payload_ and indicates the new value for the date.

### Look at Use of `DateInput` Component in `App.vue`

- Open `src/entrypoints/FD3_Activity/App.vue`
- Notice in the use of `DateInput`
  ```js
  <DateInput
    v-bind:initDate="date"
    v-on:date-changed="date = $event"
  />
  ```
  - `v-bind:initDate="date"`
    - Sets the value of the `initDate` prop to be the value of the `date` property in the Vue `data`.
      - The default value is set as `date: '2019-06-15',` 
  - `v-on:date-changed="date = $event"`
    - Sets the event handler for the `date-changed` event from the `DateInput`.
    - The event handler sets the value of the `date` property in the Vue `data` to be the payload of the event (i.e. the new date).

### Big Picture

To summarize all of that more briefly:
- The Harvest form uses `v-bind` to pass the initial date to the `DateInput` component via its `initDate` prop.
- When `pickedDate` changes in the `DateInput` component, the component emits a `date-changed` event with the new date as the event payload.
- When the Harvest form receives a `date-changed` event, the event handler updates the `date` property in its Vue `data`.

## One Way vs Two Way Binding

Let's compare how we are using the `DateInput` to how we are using other HTML inputs
- `DateInput` uses `v-bind` and `v-on` to send and receive values. 
  ```js
  <DateInput
    v-bind:initDate="date"
    v-on:date-changed="date = $event"
  />
  ```
- All of the HTML inputs use `v-model`.
  - The "Crop" select just uses `v-model`.
  - The "Plant" radio buttons use `v-model`.
  - The "Quantity" input uses `v-model`.
  - The "Unit" select uses `v-model`.
  - The "Comment" input uses `v-model`.

Recall that Vue has both _one way_ binding and _two way_ binding.
- `v-model` is two way binding.
  - If the "Crop" select changes the value of `crop` in the Vue `data` changes.
  - If the value of `crop` in the Vue `data` changes then the "Crop" select changes.
- `v-bind` is one way binding.
  - If the `date` value in the Vue `data` changes then the `initDate` prop changes and the date in the `DateInput` changes. But not vice versa.
  - So, we had to add the `v-on` so that if the date in the `DateInput` changes then the `date` in the Vue `data` will change.
    - Using `v-bind` and `v-on` is a way to create a two way data binding.

**`v-model` is a syntactic shortcut for `v-bind` and `v-on`.**

## Enabling Two Way Binding with `v-model` for Vue Components

It would be a shame if using Vue components forced us to use the more cumbersome `v-bind` and `v-on` approach to creating two way binding. So Vue provides a way to make custom components work with `v-model` as well. We just need use the following _convention_.

**If we want to use `v-model` with a prop named `abc` then the event emitted when the value of `abc` changes must be named `update:abc`.**

### Enabling Two Way Binding in `DateInput`

To see how this works, let's modify our `DateInput` component so that we can used `v-model` to instead of `v-bind` and `v-on`.

- Use the `09-FD3-Tutorials-Soln` branch
- In `DateInput.vue`
  - Change:
    - `emits['update:initDate']`
    - `this.$emit('update:initDate', this.pickedDate);`
      - Using the convention.
- In `App.vue`
  - Change:
    - `<DateInput v-model:initDate="date" />`
- Demo Two Way Binding using Vue Devtools
  - Change the "Date" input see the change in the Vue `data`.
  - Change the Vue `data` see the change in the "Date" input.

### Improving the Code (reducing technical debt)

This was a good example of a _refactoring_.
- A _refactoring_ is a change in the implementation of the code to improve it without changing the behavior of the system.

But we have introduced some strange semantics:
- The `initDate` prop is not really the _initial date_ any more.
- A new reader of the code/docs might reasonably assume based on the name that this prop can only be used to set the initial date of the component.
- So we should take the time to fix it.
  - Takes us maybe 2 minutes.
  - Might over time cost 10-20 developers a few minutes of confusion each?
  - Overall its an efficiency win for the project.
    - A little of your time saves a lot of time overall.

To clean up these semantics let's rename the prop to be `date` instead.
- Note: This can be skipped if time is getting short. 
  - It is already implemented in the `10-FD2-Activity-Starter` branch.
- In `DateSelect.vue` 
  - Change:
    - `props: ['date'],`
    - `emits: ['update:date']`
    - `this.$emit('update:date', this.pickedDate);`
- In `App.vue
  - `v-model:date="date"`
- Rebuild `school` module
- Use Vue Devtools to demo that two way binding still works.
  - Note: When rebuilding, often you need to close and reopen the Vue Devtools to get them to connect to the new Vue instance.
    - Can also use the hack of clicking "<-" and "->" arrows in the Devtools pane and then refresh the Devtools.

## The FarmData2 Components

You built the `DataInput` component so that you understand how components work. When creating forms in FarmData2 you'll often be using existing components that are provided by FarmData2.

- Point out the `components` directory
  - Each component has a folder:
    - Look at `components/DateSelector`
      - The `DateSelector.vue` file - like our `DateInput.vue` file, just a little more complicated.
      - Also a bunch of `*.comp.cy.js` files that contain tests.
  - Some other components
    - `CommentBox`, `CropSelector`, `SubmitResetButtons` ...
  - Each is used on many forms.

Each time there is a need for a new UI component in FarmData2 a new custom Vue component is created and tested.
- This provides multiple benefits:
  - Encapsulation - Ability to isolate issues and features.
  - Consistency - UI components look and behave the same everywhere.
  - Testing - Ability to test the component independently from the forms that contain it.

### The Component Documentation

There is documentation for these components that will help us when we want to use them in new forms.

- Start the Documentation Server
  - Open a new terminal pane.
  - `npm run docs:view
- Navigate to the "FarmData2 Documentation"
  - Components documentation is in the table at the top of the page.
    - Library docs that you were using are at the bottom.

The page for each component will have a similar structure:
- Visit `DateSelector`
  - A short description.
  - A Link to a live running example that you can play with.
  - A Usage Example showing how to incorporate it into a form.
  - A table of `data-cy` attributes used for testing.
    - More on that in the next tutorial!
  - A table of the props that the component offers for input.
    - The `required` and `showValidityStyling` props are common to all of the FarmData2 components.
      - More on those in a moment.
    - Indicates any default values that are used if the prop is omitted when the component is used in a form.
  - A table of the events that the component emits as output.
    - Note the `update:date` event.
      - This is how we know we can use `v-model` (instead of `v-bind` and `v-on`) with the `date` prop to create a two way binding.
    - The `ready` and `valid` events are common to all FarmData2 components.
      - `ready` is a technical detail needed for testing.
      - More on `valid` in a moment.

#### The "Live Example"

The "Live Example" links in the documentation take you to a page from the "FD2 Examples" menu for the component. These pages provide a way to:
- experiment with the components to learn more about the way they work.
- manually test components when they are being built and modified.

The `DateSelector` Live Example page contains:
- An instance of the component that you can interact with.
- A table that let's you manipulate the props being passed to the component from this page.
- A table showing the events and the most recent payloads that the component has emitted.

- Demo:
  - `required`: puts the `*` in to indicate that the component is required.
    - Click it on and off.
  - `showValidityStyling`: determines if the input element is styled to show if the value is valid or not.
    - Click it on, shows valid input with green check.
    - Delete the day to create an invalid date.
      - Shows red X and feedback text indicating "A valid date is required."
    - Click it off, styling goes away.
    - FarmData2 forms use this to give the user feedback on the validity of the form inputs at appropriate times.
  - `valid`: Indicates if the value in the component is valid.
    - Pick a valid date.
      - `date` (`update:date`) event will show `true`.
      - `valid` event will show `true`.
    - Delete the day to create an invalid date.
      - `date` event will show _blank_ (`''`).
      - `valid` event will show `false`.
    - Note that we are seeing another example of how building the components helps with encapsulation, consistency and testing.
      - The logic for computing if the component's value is valid is encapsulated in the component. 
      - Because the logic is encapsulated in the component:
        - It does not need to be repeated on every page that uses the component.
          - For the `Date` component this is relatively simple.
          - But for other components it can be much more complicated.
        - It will be consistent on every page that uses the component.
        - It can be tested once for the component, rather than on every page that uses the component.

### The `CropSelector`

- If time is too tight this can be skipped.
- Look at `CropSelector` Documentation
  - Note that the component fetches the list of crops from farmOS.
  - More encapsulation, consistency and testing advantages.
  - Also simplifies the `App.vue` pages because they don't need to do the fetch.
    - You'll be converting some of your HTML components to FarmData2 components in the Activity and the Application assignments.

## What Now?

What you'll be doing in the hands-on Activity and the Application assignment is:
- Activity: 
  - Refactoring the Harvest form to use a FarmData2 `DateSelector` instead of your `DateInput`.
- Application: 
  - Continuing to refactor the Harvest form to replace the following plain HTML elements with FarmData2 components:
    - "Crop" select.
    - "Quantity" input.
    - "Comment" input.
    - "Submit/Reset" buttons.
  
---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)

