### Seeing the JSON structure of farmOS Records

THIS WAS IN THE TUTORIAL... SO MAYBE SKIP?

When we use these _records_ in FarmDat2 we will access them via functions in the `farmosUtil` library that make use of the farmOS API. These functions all return JSON objects or arrays of JSON objects (e.g. as you saw with `getCrops` in the tutorial).

To use the records it will be helpful to be able to see the structure of the JSON.
- You can get the records and use `console.log` as you did in the tutorial.
- You can also use the `npm run printlog` script.
  - ```
    npm run printlog
    ```
    - Shows all of the different types of records that exist.
      - Note the `asset--`, `log--`, `quantity-`, `taxonomy_term--` prefixes
      - Note the `plant`, `harvest`, `standard`, `plant_type`, and `unit` suffixes.
  - Can look at the JSON structure for a specific record by adding its name:
    - ```
      npm run printlog log--harvest
      ```
      - Shows the structure of the harvest log record.
        - Note `attributes`
          - `name`, `timestamp`, `status`, `notes`, etc.
        - Note `relationships`
          - `location`, `asset`, `category`, `quantity`, etc.
      - Can also use:
        - `asset--plant`
        - `taxonomy_term--plant_type`
        - `taxonomy_term--unit`
        - etc.