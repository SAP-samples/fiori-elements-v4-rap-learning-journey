### Exercise: Add Plane Details Section to the Subobject Page Body

##### After completing the exercise, the `annotation.xml` file should look like the one below:

##### Instructions:

1. Look for changes in the file located at travels > webapp > annotations > annotation.xml under the specified `<Annotation>` and `<Record>` tags.
2. Refer to **Solution A** for UI.Identification annotation added for identification section.
3. Refer to **Solution B** for UI.Facets record added to reference the UI.Identification annotation.

<details>
    <summary>Solution A:</summary>

```abap
<Annotation Term="UI.Identification">
    <Collection>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="_Flight/PlaneType"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="_Flight/OccupiedSeats"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="_Flight/MaximumSeats"/>
        </Record>
    </Collection>
</Annotation>
```
</details>
<details>
    <summary>Solution B:</summary>

```abap
<Annotation Term="UI.Facets">
    <Collection>
        <Record Type="UI.ReferenceFacet">
            <PropertyValue Property="Label" String="{@i18n>planeDetails}"/>
            <PropertyValue Property="ID" String="PlaneDetails"/>
            <PropertyValue Property="Target" AnnotationPath="@UI.Identification"/>
        </Record>
    </Collection>
</Annotation>
```
</details>