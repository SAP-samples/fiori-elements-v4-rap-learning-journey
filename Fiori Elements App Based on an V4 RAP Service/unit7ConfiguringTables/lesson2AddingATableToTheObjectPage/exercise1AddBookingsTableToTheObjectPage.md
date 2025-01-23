### Exercise: Add a Bookings Table to the Object Page

##### After completing the exercise, the `annotation.xml` in the `travels > webapp > annotations` folder should look like the one below:

##### Replace all the occurances of `######` with the unique package number assigned to your project.

##### In this exercise, the `UI.ReferenceFacet` record is added to display a new section called "Bookings". A `UI.LineItem` annotation is added for the Booking entity with all the relavant records. The `Common.Text` annotation is added for 'CarrierID' and a `UI.TextArrangement` annotation with `TextOnly` is applied to 'CustomerID'.
   
<details>
    <summary>Solution:</summary>

```abap
 <edmx:Edmx xmlns:edmx="http://docs.oasis-open.org/odata/ns/edmx" Version="4.0">
    <edmx:Reference Uri="https://sap.github.io/odata-vocabularies/vocabularies/Common.xml">
        <edmx:Include Namespace="com.sap.vocabularies.Common.v1" Alias="Common"/>
    </edmx:Reference>
    <edmx:Reference Uri="https://sap.github.io/odata-vocabularies/vocabularies/UI.xml">
        <edmx:Include Namespace="com.sap.vocabularies.UI.v1" Alias="UI"/>
    </edmx:Reference>
    <edmx:Reference Uri="/sap/opu/odata4/sap/zui_fe_travel_######_o4/srvd/sap/zui_fe_travel_######_o4/0001/$metadata">
        <edmx:Include Namespace="com.sap.gateway.srvd.zfe_travel_######.v0001" Alias="SAP__self"/>
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
            </Annotations>
            <Annotations Target="SAP__self.BookingType/CustomerID">
                <Annotation Term="Common.Text" Path="_Customer/LastName">
                    <Annotation Term="UI.TextArrangement" EnumMember="UI.TextArrangementType/TextOnly"/>
                </Annotation>
            </Annotations>
            <Annotations Target="SAP__self.BookingType/CarrierID">
                <Annotation Term="Common.Text" Path="_Carrier/Name"/>
            </Annotations>
        </Schema>
    </edmx:DataServices>
</edmx:Edmx>
```
</details>