# 08 - FD2 - Tutorials

In the previous topic you learned how to access data via an API using JavaScript's `fetch` function. You then used `fetch` to retrieve the list of crops and the active plant assets for a crop from farmOS. In this tutorial you will learn about FarmData2's `farmosUtil` library.  This library contains functions that make reading and writing farmOS data more maintainable, easier to write and more reliable.

## Why have the `farmosUtil` library?

While it wasn't too bad to write code to fetch the crops and plants, there were a lot of details to get right (e.g. the URL, the query parameters). And, if you think about it, the code for retrieving crops and plants (and lots of other things) is likely to be used in many places throughout the FarmDat2 application. Thus, it makes sense to factor out such reusable code into functions. FarmData2 collects these functions into its `farmosUtil` library. Then all of the code in FarmData2 that needs to access farmOS data does so by calling functions in the `farmosUtil` library.

Factoring out these functions into the `farmosUtil` library has a number of advantages:
- It makes the code more maintainable by eliminating duplicate code and making the reading and writing of data more consistent across the code base.
- It makes it easier for developers to read and write farmOS data by allowing them to call functions and pass parameters rather than remembering specific API URLs and building query parameter strings.
- It makes the code more reliable because these functions can be tested once, rather than at each place the code is used.

Now that you have an idea of why FarmData2 uses its `farmosUtil` library for accessing farmOS data, let's see how we can use.  The remainder of the tutorial will guide you through replacing the code you used to fetch the crop with a call to a `farmosUtil` library function that simplifies that work.

## Preliminaries

Note that while previous tutorials were done in a simple `index.html` file, this tutorial will be done using the Harvest Form that you have been building in the Application assignments.

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize your `development` branch with the upstream `development` branch.
3. **Don't miss this step.** Run the following commands to integrate some of the changes in `development` into the running farmOS instance.
   ```
   reinstallFD2Module.bash
   installDB.bash
   npm run docs:gen
   ```
4. Open farmOS in the browser.
5. Go to the "FD2 School" -> "FD2-Tutorial" page.
   - The "FD2 School" menu now contains options for "FD2-Tutorial", "FD2-Activity" and "FD2-Application". Your work in this Tutorial will appear in the "FD2-Tutorial" page.
6. Open the `FarmData2/modules/farm_fd2_school/src/entrypoints/FD2-Tutorials/App.vue` file file in VS Codium.
7. Verify that everything works as expected. In particular, be sure that the "Crop" select is populated with the full list of crops.

## The `farmosUtil` Library Documentation

This section introduces you to the documentation for the `farmosUtil` library. You will need to use this documentation when you want to determine if the library has a function you can use, or to refresh your memory on how to use a function that you know exists. 

Follow the steps below to find the documentation for the function that can retrieve the list of crops stored in farmOS.
1. Open a new terminal (or another tab in an existing terminal).
2. Run the following command to start the server that makes the documentation available:
   ```
   npm run docs:view
   ```
3. The above command will open new browser tab containing the documentation.
4. Scroll down to the "FarmData2 Component and Library Documentation" section.
5. Click "FarmData2 Documentation"
6. Scroll down to the "Library" section.
7. Click "farmosUtil"
8. Scroll down to the "Sections" section.
   - Notice that this section contains a long list of different categories of utility functions that are provided by the library.
9. We are interested in fetching the crops.
   - Find the section for crops.
   - Click on `crops`.
10. Look at the functions in the `crops` section and see if you can answer the following questions for yourself.
    - How many functions are there that deal with crops?
    - Which of those functions do you think we'll want to use?
11. Because we want to get the crops we will want to use the `getCrops()` function. So, click `getCrops()`.
12. Skim over the documentation for the `getCrops` function and see if you can answer the following questions for yourself.
    - Does the `getCrops` function require any parameters?
    - What type of data does the `getCrops` function return.
    - How is the returned data ordered?
13. The answers:
    - Does the `getCrops` function require any parameters?
      - No. the empty `()` after the function name indicate that there are no parameters.
    - What type of data does the `getCrops` function return.
      - It returns an array of objects. The objects are of type `taxonomy_term--plant_type`.
    - How is the returned data ordered?
      - The objects are in sorted order by the `attributes.name` property.

## Using the `getCrops` Function

In this section you will simplify the code by replacing the code that uses `fetch` to get the list of crops directly from the API endpoint with code that uses the `getCrops` function in the `farmosUtil` library.

### Importing the `farmosUtil` Library

In order for code in your Vue instance to use functions in the `farmosUtil` library it is necessary to import that library into you Vue instance. Importing libraries in JavaScript's is similar to using `import` in Java or Python or `include` in C/C++, if you are familiar with those languages.

1. Add the statement to import the farmosUtil library just after the `<script>` tag and just before the start of your Vue instance as shown below
   ```
   <script>
   import * as farmosUtil from '@libs/farmosUtil/farmosUtil';
   export default { 
     ... 
   }
   </script>
   ```
2. Note that the linter will complain because you have declared `farmosUtil` but you have not use it.  We'll fix tht in the next section.

### Removing the code that uses `fetch`

Let's get rid of the code that uses `fetch` to get the list of crops and confirm that the "Crop" select is no longer populated.

1. Find the `created` lifecycle hook where you added the code that uses `fetch` to retrieve the list of crops.
2. Comment out all of the code in the `created` lifecycle hook.
3. rebuild the FD2 School module, reload the page, and confirm that the "Crop" select now is not populated with the crop list.

### Fetching the Crops using `getCrops`

Now let's use the `getCrops` function and look at the result that we get back.

1. Add the following code to the `created` lifecycle hook.
   ```
   const cropsArray = await farmosUtil.getCrops();
   console.log(cropsArray);
   ```
   This code uses the `getCrops` function to fetch crops and logs the array of `taxonomy_term--plant_type` objects to the console.
2. Open the "console" tab of the Developer Tools.
3. Rebuild the FD2 School module and reload the page.
4. Explore the array of `taxonomy_term--plant_type` objects that is logged to the console.  See if you can answer the following questions for yourself.
   - What is the name of the crop that is at index 0? Index 5?
   - Using the `cropsArray` variable, how would you write the path to the name of the crop at the 5th index using dot notation?
  - How would you express that path using the variable `crop` if it pointed directly to object at index 5?
5. Answers:
   - What is the name of the crop that is at index 0? Index 5?
     - "ARUGULA" is at index 0 and "BROCCOLI" is at index 5.
   - Using the `cropsArray` variable, how would you write the path to the name of the crop at the 5th index using dot notation?
     - `cropsArray[5].attributes.name`
   - How would you express that path using the variable `crop` if it pointed directly to object at index 5?
     - `crop.attributes.name`

Note that logging an object to the console is an effective way to learn about the structure of the objects that are returned from the `farmosUtil` libraries. Looking at these object will help you build dot notation paths to use to access the specific properties that you need.

You can also use the `npm run printlog` command to display the JSON structure of a specific farmOS type. For example, the following command will display the JSON structure of the `taxonomy_term--plant_type`.
```
npm run printlog taxonomy_term--plant_type`
```

### Setting the `cropList`

Now that we now we are getting the correct array of objects from our call to `getCrop` we can use it to set the `cropList` in the Vue `data`.

1. Add the following line to the `created` lifecycle hook to set the `cropList` property in the Vue `data` using the crops that were fetched by the `getCrop` function.
```
this.cropList = cropsArray;
```
2. Rebuild the FD2 School module and reload the page.
3. Confirm that the "Crops" select is now populated again.
4. Commit your changes to your feature branch.

## Clean Up

Now that the page is working again we can clean up a few things.

1. The page contains a computed property `sortedCrops` that was used to ensure that the `<option>` elements in the "Crop" select appeared in alphabetical order.  But we now know that the crops in the result returned from the `getCrop` function are already sorted (how convenient :).  Remove the `sortedCrops` computed function and adjust the code so that the "Crops" select is still populated in alphabetical order.
2. Rebuild the FD2 School module and reload the page.
3. Confirm that the options in the "Crops" select are still in alphabetical order..
4. Commit your changes to your feature branch.
5. Remove the commented out code and the `console.log` statement from the `created` lifecycle hook.
6. Commit your changes to your feature branch.

## Checklist

- Thg `farmosUtil` library is imported.
- The `created` lifecycle hook uses the `getCrops` function from the `farmosUtil` library to fetch the crops and set the `cropList`.
- The `sortedCrops` computed property has been removed.
- The original `created` lifecycle hook code has been removed.
- The `console.log` statement used for testing has been removed.
- The "Crop" select is populated with the alphabetized list of crops.

## Turning In Your Work

The [Git/GitHub Reference](../GitReference/GitReference.md) may be handy here if you don't remember the necessary commands.

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your origin repo.
3. Go to your origin repo on GitHub.
4. Make a PR to the `development` branch in the upstream repository.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR to ensure that you have made only the necessary changes in your `FD2-Tutorial/App.vue` file.  Make any necessary changes, commit them to your feature branch and push it again to update the PR.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)