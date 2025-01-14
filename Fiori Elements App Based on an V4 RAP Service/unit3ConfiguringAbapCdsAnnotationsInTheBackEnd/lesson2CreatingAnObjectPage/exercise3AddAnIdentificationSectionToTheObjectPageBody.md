### Exercise: Add an Identification Section to the Object Page Body

##### After completing the exercise, the metadata extension file for Travel entity, `ZC_FE_TRAVEL_######` should look like the one below:

##### Replace all the occurances of ###### with the unique package number assigned to your project.

<details>
    <summary>Solution:</summary>

```abap
@Metadata.layer: #CORE
@UI.headerInfo: {
    typeNamePlural: 'Travels',
    typeName: 'Travel',
    title: { type: #STANDARD, value: 'Description' },
    description: { type: #STANDARD, value: 'TravelID' }
}
annotate view ZC_FE_Travel_######
with
{
    @UI.facet: [{
        purpose: #HEADER,
        position: 10,
        type: #DATAPOINT_REFERENCE,
        targetQualifier: 'PriceData'
    },
    {
        purpose: #HEADER,
        position: 20,
        type: #DATAPOINT_REFERENCE,
        targetQualifier: 'StatusData'
    },
    {
        label: 'General Information',
        type: #COLLECTION,
        id: 'GeneralInfo',
        position: 10
    },
    {
        label: 'General',
        type: #IDENTIFICATION_REFERENCE,
        parentId: 'GeneralInfo' /* The section id */
    }]

    @UI.lineItem: [{position: 10}]
    @UI.selectionField: [{position: 10}]
    TravelID;

    @UI.lineItem: [{position: 20}]
    @UI.selectionField: [{position: 20}]
    @UI.identification: [{position: 10}]
    AgencyID;

    @UI.lineItem: [{position: 30}]
    @UI.selectionField: [{position: 30}]
    @UI.identification: [{position: 20}]
    CustomerID;

    @UI.lineItem: [{position: 40}]
    BeginDate;

    @UI.lineItem: [{position: 50}]
    EndDate;

    @UI.lineItem: [{position: 60}]
    BookingFee;

    @UI.lineItem: [{position: 70}]
    @UI.dataPoint: { qualifier: 'PriceData', title: 'Total Price' }
    TotalPrice;

    @UI.lineItem: [{position: 80, criticality: 'OverallStatusCriticality'}]
    @UI.textArrangement: #TEXT_ONLY
    @UI.dataPoint: { qualifier: 'StatusData', title: 'Status', criticality: 'OverallStatusCriticality' }
    OverallStatus;

    @UI.lineItem: [{position: 90}]
    LastChangedAt;
}
```
</details>