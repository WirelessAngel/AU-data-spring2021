# Assignment 5: Interview a dataset
## "Interview" a dataset with three specific, interesting questions.

####Turn in:

A link to the dataset (which you can include in your repository), your questions, as well as the answers to those questions.

[title of link](url)

### Questions:

How has the rental landscape changed from before the financial crisis (2007) until now (2021)? 

Has there been a decline in single family units and an increase in apartments? The time difference is such that there is unlikely to be a decline. However, we might be able to see if the number of single family units has increased at the same rate of apartment units.




Write down all steps used to clean and analyze the data, including any Excel formulas.

I secured the current Integrated Tax System Public Extract (Feb. 2021) from Open Data DC and a copy of an archived version from 2007.

I deleted any columns that did not assist in answering the question at hand or similar questions (police ward, AYB, etc.)

Then I used [DC's tax use codes](https://otr.cfo.dc.gov/sites/default/files/dc/sites/otr/publication/attachments/Use%20codes.pdf) to filter out and delete any properties that were not used primarily as a place of residence.

These records did not always have unit count. So, I secured datasets from the same year which had a matching data point (SSL) that did include the number of units at a location. These were the Computer Assisted Mass Appraisal (CAMA) datasets.

Sean McMinn used Python to combine these datasets (CAMA residential, CAMA commercial, and CAMA condominium) with their respective Integrated Tax System Public Extract. CAMA condo did not have a unit count. However, each condo is a separate tax entity and accounts for a single residential unit. So, we added a unit 1 column that assigned a single unit to each condo.

I deleted any other extraneous columns that came as part of the CAMA datasets (heating type, AC, wall materials, etc.).


The dataset also includes homestead codes of 1 or 5. If a unit has this code it means the occupant has received an owner/senior owner write off on their taxes for that particular unit. Meaning they are an owner occupier and that unit is not available for rent. It is assumed that all units without this code indicated are available for rent. So, these entries are also deleted from the dataset.

# *Tomorrow*

Certain use codes are reserved for single unit dwellings. Will use either an IF (_) Then (_) statement to assign a unit number of 1 to these units -if blank- or a similar method.


Write a sample headline and nut graf based on the most interesting of the three questions.

This analysis can be related to your final project, but does not have to be.

