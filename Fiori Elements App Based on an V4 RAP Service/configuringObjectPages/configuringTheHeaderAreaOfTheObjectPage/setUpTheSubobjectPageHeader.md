### Exercise: Set Up the Subobject Page Header

##### After completing the exercise, the `annotation.xml` file should look like the one below:

##### Instructions:

1. Look for changes in the file located at travels > webapp > annotations > annotation.xml under the specified `<Annotation>` and `<Record>` tags.
2. Refer to **Solution A** for the UI.HeaderInfo annotation added for header.
3. Refer to **Solution B** for the UI.headerFacets records added for 5 data point sections, where each refers to a corresponding UI.DataPoint annotation.
   
<details>
    <summary>Solution A:</summary>

```abap
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
```
</details>

<details>
    <summary>Solution B:</summary>

```abap
<Annotation Term="UI.HeaderFacets">
    <Collection>
        <Record Type="UI.ReferenceFacet">
            <PropertyValue Property="ID" String="AirlineID_Text"/>
            <PropertyValue Property="Target" AnnotationPath="_Connection/@UI.DataPoint#AirlineID_Text1"/>
        </Record>
        <Record Type="UI.ReferenceFacet">
            <PropertyValue Property="ID" String="DepartureTime"/>
            <PropertyValue Property="Target" AnnotationPath="_Connection/@UI.DataPoint#DepartureTime2"/>
        </Record>
        <Record Type="UI.ReferenceFacet">
            <PropertyValue Property="ID" String="DepartureAirport"/>
            <PropertyValue Property="Target" AnnotationPath="_Connection/@UI.DataPoint#DepartureAirport2"/>
        </Record>
        <Record Type="UI.ReferenceFacet">
            <PropertyValue Property="ID" String="ArrivalTime"/>
            <PropertyValue Property="Target" AnnotationPath="_Connection/@UI.DataPoint#ArrivalTime1"/>
        </Record>
        <Record Type="UI.ReferenceFacet">
            <PropertyValue Property="ID" String="DestinationAirport"/>
            <PropertyValue Property="Target" AnnotationPath="_Connection/@UI.DataPoint#DestinationAirport1"/>
        </Record>
    </Collection>
</Annotation>
```

```abap
<Annotation Term="UI.DataPoint" Qualifier="DepartureTime2">
    <Record Type="UI.DataPointType">
        <PropertyValue Property="Value" Path="DepartureTime"/>
        <PropertyValue Property="Title" String="{@i18n>departureTime}"/>
    </Record>
</Annotation>
<Annotation Term="UI.DataPoint" Qualifier="DepartureAirport2">
    <Record Type="UI.DataPointType">
        <PropertyValue Property="Value" Path="DepartureAirport"/>
        <PropertyValue Property="Title" String="{@i18n>departureAirport}"/>
    </Record>
</Annotation>
<Annotation Term="UI.DataPoint" Qualifier="ArrivalTime1">
    <Record Type="UI.DataPointType">
        <PropertyValue Property="Value" Path="ArrivalTime"/>
        <PropertyValue Property="Title" String="{@i18n>arrivalTime}"/>
    </Record>
</Annotation>
<Annotation Term="UI.DataPoint" Qualifier="DestinationAirport1">
    <Record Type="UI.DataPointType">
        <PropertyValue Property="Value" Path="DestinationAirport"/>
        <PropertyValue Property="Title" String="{@i18n>destinationAirport}"/>
    </Record>
</Annotation>
<Annotation Term="UI.DataPoint" Qualifier="AirlineID_Text1">
    <Record Type="UI.DataPointType">
        <PropertyValue Property="Value" Path="AirlineID_Text"/>
        <PropertyValue Property="Title" String="{@i18n>airline}"/>
    </Record>
</Annotation>
```
</details>

