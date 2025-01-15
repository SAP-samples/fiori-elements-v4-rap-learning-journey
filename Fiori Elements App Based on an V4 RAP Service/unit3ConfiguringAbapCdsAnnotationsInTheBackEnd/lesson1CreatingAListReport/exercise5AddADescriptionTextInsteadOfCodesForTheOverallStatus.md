### Exercise: Add a Description Text Instead of Codes for the Overall Status

##### After completing the exercise, the ABAP CDS projection view file for Travel entity, `ZC_FE_TRAVEL_######` should look like the one below:

##### Replace all the occurances of ###### with the unique package number assigned to your project.

<details>
    <summary>Solution:</summary>

```abap
@AccessControl.authorizationCheck: #CHECK
@Metadata.allowExtensions: true
@EndUserText.label: 'Projection View forTravel'
@ObjectModel.semanticKey: [ 'TravelID' ]
@Search.searchable: true
define root view entity ZC_FE_Travel_######
  as projection on ZI_FE_Travel_######
{
  key TravelUUID,
  @Search.defaultSearchElement: true
  @Search.fuzzinessThreshold: 0.90 
  TravelID,
  @Consumption.valueHelpDefinition: [ {
    entity: {
      name: '/DMO/I_Agency', 
      element: 'AgencyID'
    }
  } ]
  AgencyID,
  CustomerID,
  BeginDate,
  EndDate,
  @Semantics.amount.currencyCode: 'CurrencyCode'
  BookingFee,
  @Semantics.amount.currencyCode: 'CurrencyCode'
  TotalPrice,
  @Consumption.valueHelpDefinition: [ {
    entity: {
      name: 'I_Currency', 
      element: 'Currency'
    }
  } ]
  CurrencyCode,
  Description,
  _TravelStatus.TravelStatusText as TravelStatusText,
  @ObjectModel.text.element: ['TravelStatusText']
  OverallStatus,
  OverallStatusCriticality,
  CreatedBy,
  CreatedAt,
  LastChangedBy,
  LastChangedAt,
  LocalLastChangedAt,
  _Booking : redirected to composition child ZC_FE_Booking_######,
  _Agency,
  _Currency,
  _Customer,
  _TravelStatus
  
}
```
</details>

##### After completing the exercise, the metadata extension file for Travel entity, `ZC_FE_TRAVEL_######` should should look like the one below:

##### Replace all the occurances of ###### with the unique package number assigned to your project.

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

    @UI.lineItem: [{position: 80, criticality: 'OverallStatusCriticality'}]
    @UI.textArrangement: #TEXT_ONLY
    OverallStatus;

    @UI.lineItem: [{position: 90}]
    LastChangedAt;
}
```
</details>