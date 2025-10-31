

## Vue Components

- Props -> Inputs / Parameters
  - Used `v-bind` to send date into the component.
- Events -> Outputs / Return
  - Used `v-on` to have component return new date.
- Look at the date input as an example.
      - If `date` in the Vue instance changes then the component's `initDate` prop changed.
      - If the component emits a `date-updated` event with a new date the `date` in the Vue data is updated.

### Recall Two Way Binding with `v-model`

- What we have done with `v-bind` and `v-on` is to create a _two way binding_.
  - This is works.
  - But it is also done very commonly.
  - So common that Vue has the `v-model` directive.
    - `v-model` is a shorthand that creates a two way binding without us having to handle the event explicitly.
    - Look at the Crop `select` 
      - It does not have `v-bind` and `v-on`
        - It could and that would work.
      - Instead it uses `v-model`.
        - If the value of `crop` is changed in the Vue `data` then the UI will change.
        - If the selected crop in the UI changes then the value of `crop` in the Vue `data` will change.

### Enabling Two Way Binding in a Vue Component

To use `v-model` with a prop named `date` the event emitted when the date changes must be named `update:date`.

Let's modify our `DateInput` component so that we can used `v-model` to instead of `v-bind` and `v-on`.
- In component:
  - Change prop name to `date`
    - Could do it with `initDate` but the semantics aren't good.
  - Change initialization of `pickedDate` to use `date`
  - Change event name to `update:date`
    - In `emits`
    - In `this.$emit`
- In `App.vue`
  - Change `v-bind` to `v-model`
    - Just replace `v-bind` `v-model` directive but must specify the prop.
  - Remove `v-on`
- Rebuild `school` and reload page.
  - Use Devtools to show `date` is updated in the Vue `data` of the harvest form even without the `v-on`.
  - Have noticed that when you rebuild and reload you need to close the DevTools and reopen them to get the values to update.
  
## The FarmData2 Components

You built the `DataInput` component so that you understand how components work. When creating forms in FarmData2 you'll often be using existing components that are provided by FarmData2.

Each time there is a need for a new UI component in FarmData2 a new custom Vue component is created and tested.

- Point out the `components` directory
- Each component has a folder that contain the `.vue` and tests.
- Some components
  - `DateSelector`, `CropSelector`, `SubmitResetButtons` ...
  - Each is used on many forms.

## The Component Documentation 

- Show the main docs page.
  - Visit `DateSelector`
  - Link to a live example
    - Demo the page a little
      - We'll care about
        - `date` prop
        - `update:date` event
        -  Note -> can use `v-model` with `date` prop!
  - `data-cy` Attributes
    - Have to do with testing, more later
  - Table of props
    - `date`
    - `required`
    - `showValidityStyling`
    - Note default values that will be used if the prop is not bound to a value.

    - The `required` and `showValidityStyling` props are common to all of the FarmData2 components.
      - Demo on Live Example Page:
        - `required`: puts the `*` in and affects how validity is computed.
        - `showValidityStyling`: determines if the input element is styled to show if the value is valid or not.

  - Table of events
    - Note the `update:date`
      - So can use `v-model:prop` to make it work.
    - `ready` and `valid` are common to all FarmData2 components. 
      - `ready`: Related to testing so we know the component  is ready before we test it.
      - `valid`: Indicates if the value in the component is valid.
      - We won't be using these right now.

    Source is the definitive doc.

Look at the Example Page too.
- Just a way to play around with the props and see how the component behaves.

Look at `CropSelector`
  - Idea that the component does the fetch of the content!
  