# 07 - FD1 - Application

In this assignment you will modify the prototype Harvest form so that (most of) the data displayed in the Harvest form is fetched from farmOS rather than being hard-coded into the Vue instance. This will include the crops displayed in the "Crop" select and the plants displayed in the table when a crop is selected.

## Preliminaries

1. Restart your FarmData2 Development Environment.
2. Synchronize your `development` branch with the upstream to add the starter code for this assignment to your repository.
3. Rebuild the `fd2` module using the following command.
   ```
   npm run build:fd2
   ```
   - This new step in necessary because additional functionality has been added to FarmData2 that is needed for this application.
4. Use the "FD2 School" menu to navigate to the "FD1" page.
   - This page will contain a working solution to the Vue3 Application assignment.
   - If you do not see the "FD1" menu or a working solution to the Vue4 Application assignment, check that you have performed steps 2, 3, and 4 correctly and try again.
5. Create a new feature branch from `development` and switch to it for your work on this assignment.
6. Open the FarmData2 folder in VSCodium.
7. Find the `modules/farm_fd2_school/src/entrypoints/FD1/App.vue` file and open it.
   - You will modify the code in the `App.vue` file to complete this assignment.

## Exploring farmOS Data

The data managed by farmOS and used by FarmData2 can be accessed through both the farmOS user interface in the browser and through a set of API endpoints in code. The `setup.bash` script that you ran when creating your development environment populated farmOS with a small set sample data that FarmData2 uses for development and testing. In this section you'll look at some of that sample data through the farmOS user interface and through an API endpoint.

### Seeing the Crops through the farmOS User Interface

1. Open farmOS in the browser and login as `manager1`.
2. Open the "Setup" menu and choose "Taxonomy"
   - A Taxonomy is a collection of terms that are used by farmOS and FarmData2.  Defining these terms in a taxonomy ensures that they are used consistently throughout the application.
   - There are many taxonomies, but the one we will be concerned with here is the "Plant type", which is a list of all of the different "crops/varieties" that we can be planted and harvested.
3. Click "List items" for the "Plant type" Taxonomy.
   - Notice that some of the names ("ARUGULA", "ASPARAGUS", "BEAN", "RADISH") correspond to crops we have hard coded into our Harvest form.
   - If you were to count the terms you would find that there are 28 different crops in the sample data.
4. Click "ARUGULA" to display more details about the arugula crop.
    - "Crop family" is another taxonomy that is used to group related crops together. For example, "Lettuce" is also in the "Leaf Vegetables" crop family.
    - The "Harvest unit" indicates the units in which the crop is harvested. So we see that arugula is harvested by the "POUND".
5. Go back to the "Plant type" taxonomy page and click "RADISH".
    - Notice that "RADISH" is:
      - in the "Tuber/Root Vegetables" crop family.
      - harvested by the "BUNCH".
    - The "Harvest unit conversions" indicate other units in which "RADISH" can be harvested and how they can be converted to "BUNCH"es.
      - The entry for "EACH" indicates that there are 5 individual radishes in a "BUNCH".
      - The entry for "POUND" indicates that 1 "POUND" of radishes is approximately the same as 1 "BUNCH" of radishes.
      - These conversions allow some crops to be harvested in different units while still being able compute the total amount that has been harvested.
        - For example, approximately how many bunches of radishes would you have if you harvested 4 "BUNCHES", 18 "EACH" and 5 "POUNDS"?
6. Click through a few more of the crops in the "Plant type" taxonomy until you have a feel for how this taxonomy works.

### Seeing the Crops through a farmOS API Endpoint

Now let's see the same "Plant type" (i.e. crop) data through an API endpoint.

1. Ensure that you are logged into farmOS as `manager1`.
2. Open another tab in the browser and visit the following URL:
   - [http://farmos/api/taxonomy_term/plant_type](http://farmos/api/taxonomy_term/plant_type)
   - The response in the browser should look as shown below.
     ![Response from the taxonomy_term/plant_type API](images/FD2-Plant-Types-API-1.png)
3. The information we are interested in is in the `data` property.
   - Click the triangle next to `data` to open it.
     - Notice that `data` is an array of 28 objects.
     - Each object represents one plant type (i.e. crop).
4. Open the objects at indices 14 and 16, which should look as follows:
   ![The objects at indices 14 and 16.](images/FD2-Plant-Types-API-2.png)
   - Notice that each of the objects has properties for:
    - `type`: `taxonomy_term--plant_type`
      - This tells us that the object is a term in the "Plant type" "Taxonomy" in farmOS.
    - `id` - long string of letters and numbers.
      - This is a [_Universally Unique Identifier_](https://en.wikipedia.org/wiki/Universally_unique_identifier) (UUID).
        - Every object in farmOS has a UUID that uniquely identifies it among all objects in all instances of farmOS in the world.
    - and also `links`, `attributes` and `relationships`.
5. Open the `attributes` properties for the crops at indices 14 and 16.
   - Notice that the `name` attribute gives us the name of the crop.
6. Open the `relationships` properties for the "RADISH" crop.
   - Notice that there are properties for `fd2_harvest_unit` and `fd2_unit_conversions`.
     - These properties contain the information about the harvest units and the conversions for the "RADISH" crop that you saw earlier in the farmOS user interface.
     - You might notice that the names of the units do not appear here. Instead, these objects contain the UUID of the taxonomy term for the unit. We'll see later that FarmData2 provides us with a convenient way to map the UUID for the unit to its name.

## Using the farmOS API Endpoints in the Harvest Form

Now let's use the farmOS API endpoints to make our Harvest form work with live data. There are a few _tricky_ details that you'll need to get right when working through this section. Information about these details that you'll need to pay close attention to are formatted in **bold face** to help draw attention to them.

### Preliminaries

1. Restart your FarmData2 Development Environment.
2. Synchronize your `development` branch with the upstream to add the starter code for this assignment to your repository.
3. Rebuild the `fd2_school` module.
4. Use the "FD2 School" menu to navigate to the "FD1" page.
   - This page will contain a working solution to the Vue4 Application assignment.
   - If you do not see the "FD1" menu or a working solution to the Vue4 Application assignment, check that you have performed steps 2 and 3 correctly and try again.
5. Create a new feature branch from `development` and switch to it for your work on this assignment.
6. Open the FarmData2 folder in VSCodium.
7. Find the `modules/farm_fd2_school/src/entrypoints/FD1/App.vue` file and open it.
   - You will modify the code in this file `App.vue` file to complete this assignment.

### Some Changes You May Notice

As you saw above, the API response that we will use to get the names of the crops is more complicated than the list of strings we had been using. This is also true of the API responses that we will use to get the list of plants that appear the table. To account for this added complexity, a few changes have been integrated into the starter code provided for this application assignment. 

The overall structure of the code and the way in which it operates is largely the same as it was before. The significant difference is that the `cropList`, `plantList` and `unitList` have been modified so that their contents reflect the structure of the farmOS API responses that will provide the corresponding data. If you understand the operation of your solution to Application 07, adapting to these changes will be reasonably straight forward.  

It is not necessary, but if you are interested in more detail about the changes that were made see the [Changes made to Match API Structure](#changes-made-to-match-api-structure) section at the end of this assignment.

### Fetching the Crops

1. Add a `created` lifecycle hook that fetches the list of crops from farmOS rather than hard coding them.
   - Hint: Adapt the code that you used in the `created` lifecycle hook in the tutorials to use this endpoint.
   - Tip: Have the `created` lifecycle hook just log the resulting object to the console so that you can check that it is working before going on.
     - **You should see the same `data` property that you saw earlier with "ARUGULA" at index 14 and "RADISH" at index 16.**
2. Update the code in the `created` lifecycle hook so that **the `cropList` in the Vue data is initially an empty array but is then set to the `data` property of the API response, which contains the array of objects representing the crops.**
   - Hint: This is similar to what you did with the `users` property in the tutorial.
3. Rebuild and reload the page.
4. Confirm that the "Crop" select now contains the full list of crops.
5. Commit the changes to your feature branch with a meaningful commit message. 

### Fetching the Plants when the Crop Changes

In our Harvest form, when the user selects a crop, we need to change the contents of the table that appears so that it display all of the plants of the selected type in the table. For example, if the user selects "RADISH" as the crop then the table should contain all of the plants of type "RADISH". In this section, you'll use a FarmData2 API endpoint to fetch all of the plants of a particular crop.

#### The `fd2_plant_assets` API Endpoint

The `fd2_plant_assets` endpoint uses query parameters to allow us to fetch plants using a variety of different criteria. In particular we can use this to fetch all of the plants for a particular crop (e.g. all the `RADISH` plants).

1. Ensure that you are logged into farmOS as `manager1`.
2. Open another tab in the browser and visit the following URL:
   - [http://farmos/api/fd2_plant_assets](http://farmos/api/fd2_plant_assets)
     - The response will contain one object for each of the plants in the sample data. 
     - There are lots of them. 
     - We'll want to narrow this down using a query parameter.
3. Modify the URL by adding the query parameter as shown below:
   - [http://farmos/api/fd2_plant_assets?crop=RADISH](http://farmos/api/fd2_plant_assets?crop=RADISH)
     - Notice that the response now contains only objects for the "RADISH" plants.

#### Displaying the Plants for the Selected Crop 

1. Add a `watch` that will run anytime the user selects a new crop.
   - Tip: Have the `watch` log the name of the selected crop (i.e. `this.crop.attributes.name`) to the console to confirm that the watch is working correctly before going on.
2. Modify the code so that **the `plantList` is initially empty and the `watch` fetches the plants of the selected crop type and places the result into the `plantList`.
   - **Hint: Use string concatenation to build the URL including the name of the selected crop as a query parameter.**
     - This is similar to the way that you fetched the selected user in the hands on activity.
   - Tips: 
     - Log the URL that you construct to the console to be sure it is correct.
     - Log the API response to the console to check that your fetch is working correctly.
     - **Careful here... this response does not have a `data` property like the one for the plant types does.**
3. Confirm that the list of plants now changes when the selected crop is changed.
4. Commit the changes to your feature branch with a meaningful commit message.

#### Optional Challenge - Bug Fixes

There are a number of little bugs that the above changes have introduced into the application. This is a common occurrence as code within a large project evolve through updates and modifications. The bullets below point out these bugs and suggest how they might be fixed. If you are interested and have the time give some of them a try.  It is recommended that you attempt them in order.

1. The names of the crops in the "Crop" select no longer appear in alphabetical order, making it difficult to find the one you want. Use a computed property to fix this in a way similar to how the table rows are sorted by date.
2. Confirm that the the bug has been fixed.
3. Commit the changes to your feature branch with a meaningful commit message. 
4. An error occurs when the reset button is clicked. To see the error
   - Open the console tab in the Devtools,
   - Pick a crop,
   - Click "Reset"

   The error occurs because the `resetForm` function changes the value of `crop`, which causes the `watch` to be called. It then attempts to use the value of `crop` crop which is `null`. Use an `if/else` statement so that the `watch` only attempts to fetch the plants if a crop has been selected and returns an empty array otherwise.
5. Confirm that the the bug has been fixed.
6. Commit the changes to your feature branch with a meaningful commit message. 
7. An error occurs when a crop with no plants is selected. You can see the error by opening the console tab in the Devtools and then selecting "ASPARAGUS" or "GRASS" (and some other crops as well). This happens because the API response from the `fd2_plant_assets` endpoint is not an array of objects representing plants.  You can see this by comparing the logged value of the response when selecting "RADISH" (which has plants) to "ASPARAGUS" (which has no plants). Use an `if` statement that checks if the response is an array and set the `plantList` either to the response or an empty array, as appropriate.
8. Confirm that the the bug has been fixed.
9. Commit the changes to your feature branch with a meaningful commit message. 
10. When a crop with no plants is selected the table and the form still appear. Fix this by changing the condition in the `v-if` that hides this content and by adding another element with a `v-if` when a crop is selected and there are no plants.
11. Confirm that the the bug has been fixed.
12. Commit the changes to your feature branch with a meaningful commit message. 

Note: The starter code for the next topic will contain all of these fixes if you want to review them later.

## Checklist

- Crops are fetched from the farmOS API in the `created` lifecycle hook.
- The "Crop" select is populated with the fetched crops.
- Plants are fetched when a new crop is selected.
- The "Plant table" is populated with the plants for the selected crop.
- All `console.log` statements have been removed.
- Optional Bug Fixes
  - The crops in the "Crop" select are alphabetized.
  - The form can be reset without generating an error.
  - Picking a crop with no plants does not generate an error.
  - When a crop with no plants is selected, the table and form are hidden an a message is displayed.

## Turning In Your Work

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your origin repo.
3. Go to your origin repo on GitHub.
4. Make a PR to the `development` branch in the upstream repository.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR to ensure that you have only made changes in the `modules/farm_fd2_school/src/entrypoints/FD1` directory. Make any necessary changes, commit them to your feature branch and push it again to update the PR.

## Changes Made to Match API Structure

The following are the details of the changes that were made to this starter code as compared to a straight forward solution to Application 07. 

- The `cropList`, `plantList` and `unitList` have been modified so that their contents reflect the basic structure of the API responses that will provide the corresponding data.
- The `v-for` statements that generate the options in the "Crop" select, the rows in the "Plant table", and the options in the "Units" select were updated to work with the new structures pf the `cropList`, `plantList` and `unitList`.
- The `v-bind` for the `value` of the "Crop" select options, the radio buttons in the "Plant table" and the "Unit" select options were changed to return the entire object rather than just its string value or its `id`.
- The initial values of the `crop`, `selectedPlant` and `unit` in the Vue `data` have been changed to `null` from empty strings or -1 to reflect that they are now objects rather than strings or an integer.
- The `resetForm` method, and the `formValid`, and `sortPlantedList` computed properties were adapted to work with the values of `crop`, `selectedPlant` and `unit` as objects rather than strings or an integer.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)