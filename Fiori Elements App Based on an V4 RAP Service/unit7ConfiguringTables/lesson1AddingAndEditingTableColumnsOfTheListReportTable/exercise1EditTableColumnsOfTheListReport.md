### Exercise: Edit Table Columns of the List Report

##### After completing the exercise, the `annotation.xml` file in the `travels > webapp > annotations > annotation.xml` directory should look like the one below:

##### In this exercise, the UI.LineItem records are added or changed. The 'Overallstatus' column is placed before the 'BookingFee' column. The description column is added in the second position.

In this exercise, the UI.LineItem records are added or changed. The 'Overallstatus' column is placed before the 'BookingFee' column. The description column is added in the second position.
<details>
    <summary>Solution:</summary>

```abap
<edmx:Edmx xmlns:edmx="http://docs.oasis-open.org/odata/ns/edmx" Version="4.0">
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
            </Annotations>
        </Schema>
    </edmx:DataServices>
</edmx:Edmx>
```
</details>