### Exercise: Add Filter Fields to the List Report

##### After completing the exercise, the metadata extension file for Travel entity, `ZC_FE_TRAVEL_######` should look like the one below:

##### Replace all the occurances of `######` with the unique package number assigned to your project.

<details>
    <summary>Solution:</summary>

```abap
@Metadata.layer: #CORE
annotate view ZC_FE_Travel_######
with
{
    @UI.lineItem: [{position: 10}]
    @UI.selectionField: [{position: 10}]
    TravelID;

    @UI.lineItem: [{position: 20}]
    @UI.selectionField: [{position: 20}]
    AgencyID;

    @UI.lineItem: [{position: 30}]
    @UI.selectionField: [{position: 30}]
    CustomerID;

    @UI.lineItem: [{position: 40}]
    BeginDate;

    @UI.lineItem: [{position: 50}]
    EndDate;

    @UI.lineItem: [{position: 60}]
    BookingFee;

    @UI.lineItem: [{position: 70}]
    TotalPrice;

    @UI.lineItem: [{position: 80}]
    OverallStatus;

    @UI.lineItem: [{position: 90}]
    LastChangedAt;
}

```
</details>