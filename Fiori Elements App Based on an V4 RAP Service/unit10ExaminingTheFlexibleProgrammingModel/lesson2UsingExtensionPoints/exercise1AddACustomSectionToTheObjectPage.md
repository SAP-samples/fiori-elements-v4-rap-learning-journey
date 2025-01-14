### Exercise: Add a Custom Section to the Object Page

##### After completing the exercise, the geo map file, `GeoMap.fragment.xml` should look like the one below:

<details>
    <summary>Solution:</summary>

```abap
<core:FragmentDefinition xmlns:core="sap.ui.core" 
    xmlns="sap.m"
    xmlns:macros="sap.fe.macros"
    xmlns:vbm="sap.ui.vbm"
    displayBlock="true">
    
    <VBox id="_IDGenVBox1">
        <vbm:AnalyticMap id="_IDGenAnalyticMap1" width="100%" xmlns:l="sap.ui.layout" height="600px" initialPosition="-47.48339103742949; 48.70365903454684;0" initialZoom="2" class="sapUiMediumMarginTop">
            <vbm:vos>
                <vbm:Routes id="_IDGenRoutes1">
                    <vbm:Route id="_IDGenRoute1" position="8.682127;50.110924;0; -73.780968;40.641766;0" color="rgb(204,0,0)" colorBorder="rgb(255,255,255)" linewidth="3" routetype="Geodesic" />
                    <vbm:Route id="_IDGenRoute2" position="-73.780968;40.641766;0; -122.389977;37.615223;0" color="rgb(255,128,0)" colorBorder="rgb(255,255,255)" linewidth="3" routetype="Geodesic" />
                    <vbm:Route id="_IDGenRoute3" position="-122.389977;37.615223;0; 8.682127;50.110924;0" color="rgb(0,153,76)" colorBorder="rgb(255,255,255)" linewidth="3" routetype="Geodesic" />
                </vbm:Routes>
                <vbm:Spots id="_IDGenSpots1">
                    <vbm:Spot id="_IDGenSpot1" position="8.682127;50.110924;0" tooltip="Frankfurt am Main (FRA)" labelType="Default" labelText="Frankfurt am Main (FRA)" labelPos="5" />
                    <vbm:Spot id="_IDGenSpot2" position="-73.780968;40.641766;0" tooltip="New York (JFK)" labelType="Default" labelText="New York (JFK)" labelPos="5" />
                    <vbm:Spot id="_IDGenSpot3" position="-122.389977;37.615223;0" tooltip="San Francisco (SFO)" labelType="Default" labelText="San Francisco (SFO)" labelPos="5" />
                </vbm:Spots>
            </vbm:vos>
        </vbm:AnalyticMap>
    </VBox>
</core:FragmentDefinition>

```
 </details>