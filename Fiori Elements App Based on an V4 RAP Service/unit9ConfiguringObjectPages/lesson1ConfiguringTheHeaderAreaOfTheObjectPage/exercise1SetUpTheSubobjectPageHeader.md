### Exercise: Set Up the Subobject Page Header

##### After completing the exercise, the `annotation.xml` file in the `travels > webapp > annotations > annotation.xml` directory should look like the one below:

##### In this exercise, the `UI.HeaderInfo` is added for header and the `UI.headerFacets` records added for 5 data point sections, where each refererences a corresponding `UI.DataPoint` annotation.
   
<details>
    <summary>Solution A:</summary>

```abap
<edmx:Edmx xmlns:edmx="http://docs.oasis-open.org/odata/ns/edmx" Version="4.0">
    <edmx:Reference Uri="https://sap.github.io/odata-vocabularies/vocabularies/Common.xml">
        <edmx:Include Namespace="com.sap.vocabularies.Common.v1" Alias="Common"/>
    </edmx:Reference>
    <edmx:Reference Uri="https://sap.github.io/odata-vocabularies/vocabularies/UI.xml">
        <edmx:Include Namespace="com.sap.vocabularies.UI.v1" Alias="UI"/>
    </edmx:Reference>
    <edmx:Reference Uri="/sap/opu/odata4/sap/zui_fe_travel_001191_o4/srvd/sap/zui_fe_travel_001191_o4/0001/$metadata">
        <edmx:Include Namespace="com.sap.gateway.srvd.zfe_travel_001191.v0001" Alias="SAP__self"/>
    </edmx:Reference>
    <edmx:DataServices>
        <Schema xmlns="http://docs.oasis-open.org/odata/ns/edm" Namespace="local">
            <Annotations Target="SAP__self.TravelType">
                <Annotation Term="UI.LineItem">
                    <Collection>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="TravelID"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="Description"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="AgencyID"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="CustomerID"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="BeginDate"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="EndDate"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Criticality" Path="OverallStatusCriticality"/>
                            <PropertyValue Property="Value" Path="OverallStatus"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="BookingFee"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="TotalPrice"/>
                        </Record>
                    </Collection>
                </Annotation>
                <Annotation Term="UI.Facets">
                    <Collection>
                        <Record Type="UI.CollectionFacet">
                            <PropertyValue Property="Label" String="General Information"/>
                            <PropertyValue Property="ID" String="GeneralInfo"/>
                            <PropertyValue Property="Facets">
                                <Collection>
                                    <Record Type="UI.ReferenceFacet">
                                        <PropertyValue Property="Label" String="General"/>
                                        <PropertyValue Property="Target" AnnotationPath="@UI.Identification"/>
                                    </Record>
                                    <Record Type="UI.ReferenceFacet">
                                        <PropertyValue Property="Label" String="Prices"/>
                                        <PropertyValue Property="Target" AnnotationPath="@UI.FieldGroup#PricesGroup"/>
                                    </Record>
                                    <Record Type="UI.ReferenceFacet">
                                        <PropertyValue Property="Label" String="Dates"/>
                                        <PropertyValue Property="Target" AnnotationPath="@UI.FieldGroup#DatesGroup"/>
                                    </Record>
                                </Collection>
                            </PropertyValue>
                        </Record>
                        <Record Type="UI.ReferenceFacet">
                            <PropertyValue Property="Label" String="{@i18n>bookings}"/>
                            <PropertyValue Property="ID" String="i18nbookings"/>
                            <PropertyValue Property="Target" AnnotationPath="_Booking/@UI.LineItem#i18nbookings"/>
                        </Record>
                    </Collection>
                </Annotation>
            </Annotations>
            <Annotations Target="SAP__self.BookingType">
                <Annotation Term="UI.LineItem" Qualifier="i18nbookings">
                    <Collection>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="_Carrier/AirlinePicURL"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="BookingID"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="BookingDate"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="CarrierID"/>
                            <PropertyValue Property="Label" String="{@i18n>airline}"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="ConnectionID"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="CustomerID"/>
                            <PropertyValue Property="Label" String="{@i18n>customer}"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="FlightDate"/>
                        </Record>
                        <Record Type="UI.DataField">
                            <PropertyValue Property="Value" Path="FlightPrice"/>
                        </Record>
                    </Collection>
                </Annotation>
                <Annotation Term="UI.HeaderInfo">
                    <Record>
                        <PropertyValue Property="TypeName" String="{@i18n>booking}"/>
                        <PropertyValue Property="TypeNamePlural" String=""/>
                        <PropertyValue Property="Title">
                            <Record Type="UI.DataField">
                                <PropertyValue Property="Value" Path="BookingID"/>
                            </Record>
                        </PropertyValue>
                        <PropertyValue Property="ImageUrl" Path="_Carrier/AirlinePicURL"/>
                    </Record>
                </Annotation>
                <Annotation Term="UI.HeaderFacets">
                    <Collection>
                        <Record Type="UI.ReferenceFacet">
                            <PropertyValue Property="ID" String="AirlineID_Text"/>
                            <PropertyValue Property="Target" AnnotationPath="_Connection/@UI.DataPoint#AirlineID_Text"/>
                        </Record>
                        <Record Type="UI.ReferenceFacet">
                            <PropertyValue Property="ID" String="DepartureTime"/>
                            <PropertyValue Property="Target" AnnotationPath="_Connection/@UI.DataPoint#DepartureTime"/>
                        </Record>
                        <Record Type="UI.ReferenceFacet">
                            <PropertyValue Property="ID" String="DepartureAirport"/>
                            <PropertyValue Property="Target" AnnotationPath="_Connection/@UI.DataPoint#DepartureAirport"/>
                        </Record>
                        <Record Type="UI.ReferenceFacet">
                            <PropertyValue Property="ID" String="ArrivalTime"/>
                            <PropertyValue Property="Target" AnnotationPath="_Connection/@UI.DataPoint#ArrivalTime"/>
                        </Record>
                        <Record Type="UI.ReferenceFacet">
                            <PropertyValue Property="ID" String="DestinationAirport"/>
                            <PropertyValue Property="Target" AnnotationPath="_Connection/@UI.DataPoint#DestinationAirport"/>
                        </Record>
                    </Collection>
                </Annotation>
            </Annotations>
            <Annotations Target="SAP__self.BookingType/CustomerID">
                <Annotation Term="Common.Text" Path="_Customer/LastName">
                    <Annotation Term="UI.TextArrangement" EnumMember="UI.TextArrangementType/TextOnly"/>
                </Annotation>
            </Annotations>
            <Annotations Target="SAP__self.BookingType/CarrierID">
                <Annotation Term="Common.Text" Path="_Carrier/Name"/>
            </Annotations>
            <Annotations Target="SAP__self.ConnectionType">
                <Annotation Term="UI.DataPoint" Qualifier="AirlineID_Text">
                    <Record Type="UI.DataPointType">
                        <PropertyValue Property="Value" Path="AirlineID_Text"/>
                        <PropertyValue Property="Title" String="{@i18n>airline}"/>
                    </Record>
                </Annotation>
                <Annotation Term="UI.DataPoint" Qualifier="ArrivalTime">
                    <Record Type="UI.DataPointType">
                        <PropertyValue Property="Value" Path="ArrivalTime"/>
                        <PropertyValue Property="Title" String="{@i18n>arrivalTime}"/>
                    </Record>
                </Annotation>
                <Annotation Term="UI.DataPoint" Qualifier="DepartureTime">
                    <Record Type="UI.DataPointType">
                        <PropertyValue Property="Value" Path="DepartureTime"/>
                        <PropertyValue Property="Title" String="{@i18n>departureTime}"/>
                    </Record>
                </Annotation>
                <Annotation Term="UI.DataPoint" Qualifier="DestinationAirport">
                    <Record Type="UI.DataPointType">
                        <PropertyValue Property="Value" Path="DestinationAirport"/>
                        <PropertyValue Property="Title" String="{@i18n>destinationAirport}"/>
                    </Record>
                </Annotation>
                <Annotation Term="UI.DataPoint" Qualifier="DepartureAirport">
                    <Record Type="UI.DataPointType">
                        <PropertyValue Property="Value" Path="DepartureAirport"/>
                        <PropertyValue Property="Title" String="{@i18n>departureAirport}"/>
                    </Record>
                </Annotation>
            </Annotations>
        </Schema>
    </edmx:DataServices>
</edmx:Edmx>
```
</details>

