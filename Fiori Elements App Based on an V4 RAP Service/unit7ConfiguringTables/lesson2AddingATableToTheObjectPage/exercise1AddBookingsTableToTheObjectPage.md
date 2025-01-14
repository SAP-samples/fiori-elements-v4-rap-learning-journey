### Exercise: Add a Bookings Table to the Object Page

##### After completing the exercise, the `annotation.xml` file should look like the one below:

##### Instructions:

1. Look for changes in the file located at travels > webapp > annotations > annotation.xml under the specified `<Record>` tags.
2. Refer to **Solution A** for the UI.ReferenceFacet record added to display a new section.
3. Refer to **Solution B** for the UI.LineItem definition, which contains the table with the records you have configured, including the record for Airline Logo that was added.
4. Refer to **Solution C** for the Common.Text annotation added for 'CarrierID' in the local annotation file.
5. Refer to **Solution D** for the UI.TextArrangement annotation with TextOnly added for 'CustomerID'.
   
<details>
    <summary>Solution A:</summary>

```abap
   <Record Type="UI.ReferenceFacet">
       <PropertyValue Property="Label" String="{@i18n>bookings}"/>
       <PropertyValue Property="ID" String="i18nbookings"/>
       <PropertyValue Property="Target" AnnotationPath="_Booking/@UI.LineItem#i18nbookings"/>
   </Record>
```
</details>

<details>
    <summary>Solution B:</summary>

```abap
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
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="ConnectionID"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="CustomerID"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="FlightDate"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="FlightPrice"/>
        </Record>
    </Collection>
</Annotation>
```
</details>

<details>
    <summary>Solution C:</summary>

```abap
    <Annotations Target="SAP__self.BookingType/CarrierID">
        <Annotation Term="Common.Text" Path="_Carrier/Name"/>
    </Annotations>
```
</details>

<details>
    <summary>Solution D:</summary>

```abap
   <Annotations Target="SAP__self.BookingType/CustomerID">
       <Annotation Term="Common.Text" Path="_Customer/LastName">
           <Annotation Term="UI.TextArrangement" EnumMember="UI.TextArrangementType/TextOnly"/>
       </Annotation>
   </Annotations>
```
</details>