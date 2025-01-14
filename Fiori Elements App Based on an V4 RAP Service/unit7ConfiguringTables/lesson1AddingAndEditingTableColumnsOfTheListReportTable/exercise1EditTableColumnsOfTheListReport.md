### Exercise: Edit Table Columns of the List Report

##### After completing the exercise, the `annotation.xml` file should look like the one below:

##### Instructions:

1. Look for changes in the file located at travels > webapp > annotations > annotation.xml under the specified `<Annotation>` and `<Record>` tags.
2. The UI.LineItem record for 'OverallStatus' is placed before 'BookingFee'.
3. The UI.LineItem record for 'Description' is added in the second position.
   
<details>
    <summary>Solution:</summary>

```abap
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
```
</details>