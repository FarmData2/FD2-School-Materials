# 07 - FD1 - Tutorials

For this activity you will ...


## Exploring farmOS Data

- Sample data
  - installed by setup.bash when you created your codes space.
  - Limited data from Dickinson farm.

- Log in as manager1
- Look at "Setup" -> "Taxonomy"
  - A Taxonomy is... collection of terms
- Taxonomies for lots of things... 
  - Let's explore "Plant type"
  - Click "List items" for  "Plant type" -> "List terms"
    - notice... Names "ARUGULA", "ASPARAGUS", "BEAN", ... "RADISH"
    - If you count there will be 28 different ones in this sample data.
  - Click "ARUGULA"
    - Notice "Crop family" - another taxonomy that creates relionships between similar types of plants.
    - Notice "Harvest unit" - "POUND"
  - Click "RADISH"
    - Notice "Crop family" - different family - "Tuber/Root Vegetables"
    - Notice "Harvest unit" - also "BUNCH"
    - Notice "Harvest unit conversions"
      - "EACH", "POUND"
        - 5 EACH = 1 BUNCH
        - 1 POUND = 1 BUNCH
      - Allows for harvesting in different units but able to convert all back to BUNCH.
  - Click a few others
    - BROCCOLI, CAULIFLOWER
  - Notice sub-types too
    - Different types of "HERB"s, "LETTUCE", "RADISH"

## Introduction to Application Programming Interfaces (APIs)

- We will access data through an API.
- watch a conceptual video introduction to the idea of an API.



## farmOS API Endpoints

- Open a browser tab and log into farmos as `manager1`

- Open another browser tab
  - Looking at the "Plant type"s though an API.
    - http://farmos/api/taxonomy_term/plant_type

      ![Response from the taxonomy_term/plant_type API](images/FD2-Plant-Types-API-1.png)

- Open `data` - notice it is an array (`[...]`)
  - notice 0-27, or 28 entries
  - Open 14 and 16
    - notice `type` `taxonomy_term--plant_type`
    - notice `id` - long string of letters and numbers
      - Unique identifier for the term.
      - ![type and id values for two plant types](images/FD2-Plant-Types-API-2.png)

  - open "attributes" for 14 and 16
      - notice `name` - what we care about...

  - open "relationships for "RADISH"
      - notice "fd2_harvest_unit", "fd2_unit_conversions"
      - Open data[0], type and id again...
        - `taxonomy_term--unit`
        - We'll worry about that more later...

## JSON introductory Tutorial

- Our programs will get JSON back...
- We need to process it...

- Watch a JSON tutorial
- JSON Intro: https://www.youtube.com/watch?v=KMLOWkGAxVc
  - 5:39
    - Python starts at 4:30 - skip it.
  - covers nested objects and nested arrays too.

- How would you access...

## Doing it in Code

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize your `development` branch with the upstream `development` branch.
3. Create a new feature branch from `development` and switch to it for your work on this assignment.
4. Use the following commands to create the starter code for the tutorials:
   ```
   cd ~/FarmData2/modules/farm_fd2_school
   cp -r 05-Vue3-Tutorials-Soln 06-Vue4
   ```
5. Open the `FarmData2` folder in VSCodium.
6. Open the `index.html` file in the `FarmData2/modules/farm_fd2_school/07-FD1` directory.
   - This `index.html` file contains the shopping list app as it should be at the start of the tutorials for today.
   - All of your work for this assignment should be with the `07-FD1` directory.
7. Open the `FarmData2/modules/farm_fd2_school/07-FD1/index.html` file in the browser.

## Fetching Data 

## Reducing Data

## Filtering Data

---
## Turning In Your Work

The [Git/GitHub Reference](../GitReference/GitReference.md) may be handy here if you don't remember the necessary commands.

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your origin repo.
3. Go to your origin repo on GitHub.
4. Make a PR to the `development` branch in the upstream repository.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR to ensure that you have made only the necessary changes in your `07-FD1` directory.  Make any necessary changes, commit them to your feature branch and push it again to update the PR.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)
