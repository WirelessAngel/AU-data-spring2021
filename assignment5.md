# Assignment 5: Interview a dataset
## "Interview" a dataset with three specific, interesting questions.

#### Turn in:

A link to the dataset (which you can include in your repository), your questions, as well as the answers to those questions.

[2007 ITS and CAMA combined dataset](https://drive.google.com/file/d/16aZMJZMMVrtHLKEzuOGtwasJGydE97dQ/view?usp=sharing)
[2021 ITS and CAMA combined dataset](https://drive.google.com/file/d/1PPDjD4QPF4yPw2peMRUI5c0gvoydWxxS/view?usp=sharing)

### Questions:

How has the rental landscape changed from before the financial crisis (2007) until now (2021)? 

Has there been a decline in single family units and an increase in apartments? The time difference is such that there is unlikely to be a decline. However, we might be able to see if the number of single family units has increased at the same rate of apartment units.

<br>
<br>


**Write down all steps used to clean and analyze the data, including any Excel formulas.**

I secured the current Integrated Tax System Public Extract (Feb. 2021) from Open Data DC and a copy of an archived version from 2007.
I deleted any columns that did not assist in answering the question at hand or similar questions (police ward, AYB, etc.)

Then I used [DC's tax use codes](https://otr.cfo.dc.gov/sites/default/files/dc/sites/otr/publication/attachments/Use%20codes.pdf) to filter out and delete any properties that were not used primarily as a rental place of residence.

These records did not always have unit count. So, I secured datasets from the same year which had a matching data point (SSL) that did include the number of units at a location. These were the Computer Assisted Mass Appraisal (CAMA) datasets.

Sean McMinn used Python to combine these datasets (CAMA residential, CAMA commercial, and CAMA condominium) with their respective Integrated Tax System Public Extract. CAMA condo did not have a unit count. However, each condo is a separate tax entity and accounts for a single residential unit. So, we added a unit 1 column that assigned a single unit to each condo.
I deleted any other extraneous columns that came as part of the CAMA datasets (heating type, AC, wall materials, etc.).


The dataset also includes homestead codes of 1 or 5. If a unit has this code it means the occupant has received an owner/senior owner write off on their taxes for that particular unit. Meaning they are an owner occupier and that unit is not available for rent. It is assumed that all units without this code indicated are available for rent. So, these entries (those with the code) are also deleted from the datasets.

### Double Checking unit counts

Some of the unit counts derived from CAMA appear to be out of line with their use codes when it comes to the original ITS file. Upon inspection of each property using google street view, it was determined that CAMA unit count should override any use code information. This is because although the use code may be technically correct for a unit at that property, in these cases there are often multiple units at the same address. CAMA gives unit count per the SSL (square suffix lot). So, it will capture the entire unit count at said address.

Upon looking at the change in numbers for each property type from 2007 to 2021, it became apparent that knowing *who* owns these rental properties is more important/newsworthy for our purposes. We will need to secure the original 2007 ITS dataset to get this information and remerge that field from the original 2021 dataset with the cleaned version.


**Write a sample headline and nut graf based on the most interesting of the three questions.**

DC bucks trend of less single family home rentals after the 2007 financial crisis.
The District of Columbia added more single family homes and conversions from 2007 to 2021 than multifamily buildings and apartments.

While many cities around the US have seen a steady increase of apartment units over rental homes; DC saw a rise in rental homes that outpaced apartments by thousands of units. The change in rental properties over time may be a unique confluence of the transcience of workers when switching administrations and the gradual gentrification of areas along with the district's development laws. The amount of multifamily units still outstrips conversions and single family units with a total of 136,061 rental units to 61,965 units. However, conversions and single family units added over 60,000 units since the financial crisis while apartments added nearly 57,000. This marks explosive growth from barely cresting 2,265 conversions and single family units in 2007.


This analysis can be related to your final project, but does not have to be.

