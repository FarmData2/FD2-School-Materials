

## Fetching the Units
- Find the function!!!

## Fetching the Plants


## Creating the Harvest Log

- console log the pickedPlant to see the json structure.

They will need some help with this...


```
      console.log(this.pickedPlant);

      const plantAsset = await farmosUtil.getPlantAsset(this.pickedPlant.uuid);

      const harvestLog = await farmosUtil.createHarvestLog(
        this.date,
        this.pickedPlant.location,
        this.pickedPlant.beds || [],
        plantAsset,
        quantity
      );
      console.log(harvestLog);
```

## Extra

- Fix issue with fetching plants that are in trays.
- Address the fact that some crops were in trays
  - use the inGround parameter of the function for fetching crops. 
- Set the measure based on the unit that was selected
  - Hint: print the unit object to the console and find the measure.
