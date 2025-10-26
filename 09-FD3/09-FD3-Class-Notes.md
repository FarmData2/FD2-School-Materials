
- Props -> Inputs / Parameters
- Evens -> Outputs / Returns

Maybe Skip?  Will we really need it?
- Look at the `this.$emit` 
  - name
  - payload - like a return value
    - Will be passed to any `v-on` handler for the event.

## Using an `update:` Event

change event name to match prop with `update:` prefix
Change element to use v-model
Remove the `v-on`

  - allows us to use `v-model` instead of `v-bind` and `v-on` as we did before.

## The FarmData2 Components

- Introduce the FD2 Components docs
  - Use the DateSelector as the example.
  - Focus on props and events.
    - Notice default values.
    - Point out `update:x` events where `x` is a `prop`
      - Means we can `v-bind`
      - Otherwise need `v-on`
  - Bush over `data-cy` information.
- Show the live example
  - From the link in the docs.
  - Connect it to the FD2 Examples menu
- Show the example code
  - Includes all props and all events.
  - You may or may not need them all.


- Might emphasize that an App.vue is just a component
  - It just doesn't have a parent - thus `<Root>`
  - it is the Main component (i.e. where things start - sort of like Java or C/C++'s `main` method.)