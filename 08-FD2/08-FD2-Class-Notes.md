# 08 - FDs - Class Notes

## Instructor ToDo Before Class

- Merge 
  - `08-FD2-Activity-Starter`
  - `08-FD2-Application-Starter`
  - `09-FD3-Tutorials-Starter`

## Questions

Take questions on the Application and Tutorial that are coming in.
- Application 07-FD1
  - Solution is in `modules/farm_fd2_school/src/endpoints/08-FD2-Tutorial-Starter`
  - Looks at crops through the:
    - farmOS User Interface (Taxonomy terms)
    - farmOS API `fd2_plant_assets` endpoint
      - http://farmos/api/fd2_plant_assets
      - http://farmos/api/fd2_plant_assets?crop=RADISH
  - Uses `fetch` to:
    - get the list of crops in the `created` lifecycle hook.
    - get the list of plants for the selected crop in a `watch`.
- Tutorial 08-FD2
  - Solution is in `module/farm_fd2_school/src/endpoints/08-FD2-Activity-Starter`
  - Introduces `farmosUtil` library
    - Functions for accessing farmOS is factored out into `farmosUtil`
    - Architected for large project with multiple developers.
      - modularization
        - independent changes
        - independent testing
        - reuse
    - Also handles
      - caching of results to reduce network traffic and increase responsiveness.
      - authentication.
  - Looked at `farmosUtil` documentation for the `getCrops` function.
  - Converted `fetch` of crops in the `created` lifecycle hook to use `farmosUtil.getCrops` function.
    - Imported the `farmosUtil` library.
    - Changed the `fetch` for crops in the `created` lifecycle hook to a call to `getCrops`.

## farmOS Record Types

Our goal in the activity and application assignments will be to make a record of a harvest by putting the data from our Harvest form into the farmOS database.  To do that we need to know a little more about the types of records that farmOS uses to store information in its database.

- The main farmOS _record types_:
  - Asset: represents a thing such a plant, equipment, land, or structure.
  - Log: represents an action such as a planting, transplanting, or harvest.
  - Taxonomy: vocabulary terms for types of assets, logs, units or other things.
  - Quantity: represents an amount and a unit associated a log, asset, or taxonomy term.

### Seeing Records in farmOS

We can see all of these record types in the farmOS user interface.

- Show:
  - "Records" -> "Assets"
    - Many different types of _things_.
      - We've seen "Plant" assets.
    - Look at a specific plant asset
      - Crop/variety -> a taxonomy term.
        - Harvest unit -> a taxonomy term.
      - Current Inventory -> a quantity.
      - Current Location -> a structure asset or land asset.
  - "Records" -> "Logs"
    - Many different types of _actions_.
      - We've seen "Seeding" logs.
    - Look at specific seeding log
      - Assets -> plant assets created by the seeding.
      - Bed Feet, Rows/Bed, Row Feed, Bed Width -> quantities.
      - Log Category -> taxonomy term.
      - Location -> a structure asset or land asset.
  - "Setup" -> "Taxonomy"
    - Many different types of _vocabularies_.
      - We've seen "Plant Type"
    - Look at the "Plant Type" -> "List terms"
      - Look at "RADISH"
        - Crop family -> a term from the "Crop family" taxonomy.
        - Harvest unit -> a term from the "Unit" taxonomy.
        - Harvest unit conversions -> a term from the "Unit" taxonomy and a conversion factor.
          - E.g. 5 EACH = 1 POUND
          - Allows for harvesting in different units.

## Creating a Harvest Log

Back to our goal of creating a record of a harvest. A harvest is an action, so we'll be creating a log to represent it.

### Using the farmOS User Interface

We can create a harvest log using the farmOS user interface to see how it works and what is involved.

- "Records" -> "Logs" -> "Harvest"
  - Currently there are no harvest logs.
  - "Add Harvest Log"
    - Name -> "Demo Harvest Log"
    - Time Stamp -> when the harvest occurred.
    - Status -> typically "done".
    - No flags.
    - No owner.
    - Notes -> our comment field.
    - Quantity:
      - Must create this to indicate how much was harvested.
      - "Add new quantity" ->  Weight, 10 POUNDS, harvest
        - N/A for Inventory adjustment.
    - "Log category" -> "harvest"
    - "Assets" -> Pick one.
    - "Equipment", "Images", "Files" -> Skip.
    - "Location" -> Pick one.
    - "Geometry" -> Skip. (GIS info if you are familiar)
    - "Is movement" -> false/off (true for transplanting)
    - "Revision" -> Skip.
    - "Save"
      - Take you to the harvest log.
  - "Records" -> "Logs" -> "Harvest"
    - We'll see that log there now.
    - Click the log name ("Demo Harvest Log")
      - All of our information is there.
  - "Records" -> "Quantities" -> "Standard"
    - The quantity we created appears here as a separate record.
    - Referenced from the harvest log.

If that seems a bit cumbersome, good! 
  - That is why FarmData2 exists! 
  - It should be pretty clear that filling out our harvest form is much quicker and easier.

### Using `farmosUtil` Library Functions

In the Harvest form you'll be using functions from the `farmosUtil` library to create the harvest log based on the data entered into the form.

- Let's find the functions we need in the `farmosUtil` docs.
  - Find `harvest`
    - Find the `createHarvestLog` function.
      - Look a the parameters.
        - `harvestDate` - we have that in our Vue `data`.
        - `locationName` & `bedNames` - we have that in our Vue `data`.
          - The object associated with the plant that is selected in the table contains this information!
        - `plantAsset`
          - Like when we created the harvest log by hand, we need to indicate the plant asset to which the harvest applies.
            - We don't have a `plant_asset` object but the object associated with the plant that is selected in the table contains the plant asset's `uuid`.
            - And if we go looking there is a `farmosUtil` function to get a plant asset given it's id (`uuid`).
            - You'll do this part in the Application assignment.
        - `quantity`
          - Like when we created the harvest log by hand, we need to create a quantity to represent the amount of the plant that was harvested.
            - We Don't have a quantity object but theres a `farmosUtil` function to create one.
            - You'll use this in the hands-on Activity.

## A Note on Calling JavaScript Functions

One `farmosUtil` function you'll be using is `getPlantsAssets`.

- Look up `getPlantAssets` in the documentation.
  - Notice parameters:
    - `locationName`
    - `checkedBeds`
    - `cropName`
    - `isInGround`
    - `isInTrays`
  - All of these have default values.
    - This allows us to call it in flexible ways.
    - If we want to look up all of the plants in a location:
      - `const plants = farmosUtil.getPlantAssets('CHUAU');`
    - If we want to look up all of the plants in a beds:
      - `const plants = farmosUtil.getPlantAssets(null, ['CHUAU-1']);`
    - If we want to look up all plants of a given crop:
      - `const plants = farmosUtil.getPlantAssets(null, [], 'RADISH');`
    - We must provide default values for any argument that precedes the one we want to use.
    - We can omit any argument that follows the one we want to use.
    - Can also use multiple parameters if we want.
      - But we typically don't need to.

## What Now?

What you'll be doing in the hands-on Activity and the Application assignment is:
- Activity: 
  - Creating the quantity record that you need to create the harvest log.
- Application: 
  - Use `farmosUtil.getPlantAssets` instead of `fetch` to get the plants for the selected crop.
  - Use a `farmosUtil` function to make the options for the "Units" select match the harvest units for the selected crop.
  - Create the harvest log.
  
---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)