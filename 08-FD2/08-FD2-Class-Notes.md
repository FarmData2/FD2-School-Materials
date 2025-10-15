
- Converted `fetch` of crops to use `farmosUtil` function.
  - Typical of FD2 Architecture
  - Code for accessing farmOS is factored out into `farmosUtil`
    - modularization
    - independent changes
    - independent testing
    - reuse
  - Handles
    - caching of results
    - authentication

- Functions exist for everything we need to record a harvest.
  - Had you use `fetch` to understand what those functions are abstracting.
  - inside every function we use
    - it calls a function in a library named `farmos.js`
    - that function then contains the `fetch` code.

- you'll explore more of those in hands on and application.

- Final goal is to create a harvest log
- Need to know about farmOS objects/
- Types of objects in farmOS
  - Logs - record actions
  - Assets - record things
  - Quantities - record amounts and units

## Creating a Harvest Log in the UI

- Demo this.
  - Show the log
  - Show the quantity
    - Show it from the log
    - Show it from the quantities menu item.

## Library Function Documentation

- Needed to create a quantity and a log.
  - was one step in the UI.

- Let's find the functions in the docs.
  - Find `harvest`
    - Find `createHarvestLog`
      - Look at parameters
      - need a plant asset
      - need a quantity 
    - Note these don't indicate `async`
      - But any function that accesses farmOS is `async`.
      - The docs just don't indicate it
        - Not sure why... its on the list to be fixed.

  - Find `quantity`
    - find `createStandardQuantity` 
    - meaning of different parameters.
    
## Calling JavaScript Functions

- positional parameters
- named parameters

- Calling function with all required parameters
  - required parameters come first.
  - others have a default value `[ ]` 
    - can be omitted.
- Calling function using named parameters.
  - If many default values and you only want to set a few
  - Can provide defaults for positional arguments
  - Can use a named parameter.
    - example...



PROBABLY SKIP FOR TIME

- Maybe show the code in the function for creating a Quantity?
  - Good argument for abstraction
  - Would be error prone and cumbersome to have that all over the place.
  - Much nicer and easier to maintain with that in one place.
  - This is part of why FD2 is needed!!!
    - farmOS is unopinionated and is very good.
    - But not tailored to specific applications.


