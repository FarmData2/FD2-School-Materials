# 07-FD1-Application Grading Checklist

- Options in the "Crop" select come from farmOS:
  - [x] - Crops are fetched in the `created` lifecycle hook.
  - [x] - "Crop" select is populated with the fetched crops.  
- Active plants come from farmOS based on selected crop:
  - [x] - Plants are fetched in a `watch` on the `crop` property.
  - [x] - Active plant table populated with plants for the selected crop.
- [x] - All `console.log` statements used for testing have been removed.
- [x] - All code commented out during development/testing has been removed.
- [x] - Work is spread across multiple commits.

## Common Feedback
- The method that you added to fetch the plants is `async`. So it should be called using `await` in your `watch`. 
  - This probably seems to work for now without `await`, but it creates a race condition that will be likely source of bugs in the future.
- The method you added to fetch the crop list is `async`.  So it should be called using `await` in your `created` lifecycle hook 
  - This probably seems to work for now without `await`, but it creates a race condition that will be likely source of bugs in the future.
- Because `await` is (or should be) used in this method or hook it needs to be declared as `async`.
- Using `.then(...)` with `fetch` works fine. Often however, and I think in this case, using `async` and `await` leads to code that is shorter, simpler and easier to understand. 