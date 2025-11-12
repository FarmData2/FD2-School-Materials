Select ASPARAGUS
Complete the form
"Submit" is enabled
Do not submit

Select ARUGULA
No ARUGULA plants
"Submit" is still enabled.

This is because the values are not cleared from the Vue data that is used by the formValid method when the crop is changed.

This part is less obvious.

Select CARROT
No CARROT plants
"Submit" is not enabled.

This is because CARROT has multiple units and when that happens the unit is set to null when the crop changes. 