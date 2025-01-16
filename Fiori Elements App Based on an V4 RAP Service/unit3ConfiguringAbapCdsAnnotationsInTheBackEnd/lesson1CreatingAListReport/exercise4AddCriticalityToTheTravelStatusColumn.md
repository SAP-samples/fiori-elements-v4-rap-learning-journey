### Exercise: Add Criticality to the Travel Status Column

##### After completing the exercise, the ABAP CDS view file for Travel entity, `ZI_FE_TRAVEL_######` should look like the one below:

##### Replace all the occurances of `######` with the unique package number assigned to your project.

 <details>
    <summary>Solution:</summary>

```abap
@AccessControl.authorizationCheck: #CHECK
@Metadata.allowExtensions: true
@EndUserText.label: 'CDS View forTravel'
define root view entity ZI_FE_Travel_######
  as select from zfe_atrav_######
  association [0..1] to /DMO/I_Agency as _Agency on $projection.AgencyID = _Agency.AgencyID
  association [0..1] to I_Currency as _Currency on $projection.CurrencyCode = _Currency.Currency
  association [0..1] to /DMO/I_Customer as _Customer on $projection.CustomerID = _Customer.CustomerID
  association [0..1] to zi_fe_stat_###### as _TravelStatus on $projection.OverallStatus = _TravelStatus.TravelStatusId
  composition [0..*] of ZI_FE_Booking_###### as _Booking
{
  key travel_uuid as TravelUUID,
  travel_id as TravelID,
  agency_id as AgencyID,
  customer_id as CustomerID,
  begin_date as BeginDate,
  end_date as EndDate,
  @Semantics.amount.currencyCode: 'CurrencyCode'
  booking_fee as BookingFee,
  @Semantics.amount.currencyCode: 'CurrencyCode'
  total_price as TotalPrice,
  currency_code as CurrencyCode,
  description as Description,
  overall_status as OverallStatus,
  case overall_status
    when 'O' then 2
    when 'A' then 3
    when 'X' then 1
    else 0
  end as OverallStatusCriticality,
  @Semantics.user.createdBy: true
  created_by as CreatedBy,
  @Semantics.systemDateTime.createdAt: true
  created_at as CreatedAt,
  @Semantics.user.lastChangedBy: true
  last_changed_by as LastChangedBy,
  @Semantics.systemDateTime.lastChangedAt: true
  last_changed_at as LastChangedAt,
  @Semantics.systemDateTime.localInstanceLastChangedAt: true
  local_last_changed_at as LocalLastChangedAt,
  _Booking,
  _Agency,
  _Currency,
  _Customer,
  _TravelStatus
  
}
```
</details>

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

    @UI.lineItem: [{position: 80, criticality: 'OverallStatusCriticality'}]
    OverallStatus;

    @UI.lineItem: [{position: 90}]
    LastChangedAt;
}
```
</details>
