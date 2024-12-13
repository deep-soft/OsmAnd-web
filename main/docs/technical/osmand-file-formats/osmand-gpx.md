---
sidebar_position: 2
---

# OsmAnd GPX

The OsmAnd's GPX file format conforms to the GPX 1.1 specification with additional data written as extensions. There are several sections of such data:

## Track appearance

The following parameters customize the appearance of a track on the map. They are used inside the "gpx" tag and apply to all tracks contained in the gpx.

#### Parameters

|Name|Spec and Purpose|
|:--------|:---------------|
|[show_arrows]|Bool. "true" or "false". Show / hide arrows along the path line.|
|[width]|String. "thin", "medium", "bold" or number 1-24. Width of the track line on the map. The thin, medium, and bold are style depended values (should be defined as currentTrackWidth attribute).|
|[color]|String. Hex value "#AARRGGBB" or "#RRGGBB". Color of a track line on the map.|
|[split_type]|String. "no_split", "distance" or "time". Split type for a track.|
|[split_interval]|Double. Split interval for a track. Distance (meters), time (seconds).|

#### Example:

```xml
<gpx version="1.1" creator="OsmAndRouterV2" xmlns="http://www.topografix.com/GPX/1/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.topografix.com/GPX/1/1 http://www.topografix.com/GPX/1/1/gpx.xsd">
...
  <extensions>
    <show_arrows>true</show_arrows>
    <color>#4e4eff</color>
    <split_type>distance</split_type>
    <split_interval>2000.0</split_interval>
    <width>bold</width>
  </extensions>
</gpx>
```

## Details of a track point (trkpt)

Written to a gpx file while recording a track.

* **speed** (meters per second)
* **heading** (0-359 degrees)

#### Example:

```xml
  <trkpt lat="52.397799" lon="4.575998">
    <ele>203</ele>
    <time>2019-05-08T10:36:43Z</time>
    <hdop>3</hdop>
    <extensions>
      <heading>273</heading>
      <speed>5.02</speed>
    </extensions>
  </trkpt>
```

## Calculated route(s)

This data contains all details of a route built with **OsmAnd** (route segments, turns, road names, road types, restrictions, etc.). The route can be completely restored as if just built, even in the absence of the respective offline maps.

A gpx file may contain several routes. Each of them is contained in a specific segment under **trkseg** / **extensions**. A gpx file is saved in this form when exporting a constructed route or when saving a track that consists of several separate segments via the [**Plan a route**](../../user/plan-route/create-route.md) functionality.

[**Plan a route**](../../user/plan-route/create-route.md) also adds one (or several, in accordance with the number of contained separate segments / tracks) **rte** blocks to the gpx file, containing route key points (**rtept**).

#### Gpx structure:

```xml
<trk>
  <trkseg>
    // List of segment points. The order of the points corresponds to the order and length of the route segments (<route><segment length="x" ... />).
    // The value of the "length" attribute corresponds to the number of points in this segment of the route.
    <trkpt ... ></trkpt>
    <extensions>
      // List of route segments
      <route>
        <segment ... />
      </route>
      // Properties of segments included in the route.
      // This data is taken from offline maps during the initial construction of a route.
      <types>
        <type ... />
      </types>
    </extensions>
  </trkseg>
</trk>

// List of intermediate route points. If there are multiple routes, the order of the rte list matches the order of the route segments.
<rte>
  <rtept ... />
    // For routes built with the "Plan route", the parameters of key points are saved.
    // If rtept is not first and last, before it (with the same idx) trkpt will be with the same data.
    <extensions>
      // Route profile type for next segment (car, bicycle, pedestrian, etc.).
      <profile>...</profile>
      // The index of the point in the gpx segment that corresponds to the first point of the calculated route for this segment.
      // If rtept is not first and last, before it (with the same idx) trkpt will be with the same data.
      <trkpt_idx>...</trkpt_idx>
    </extensions>
  </rtept>
</rte>
```

#### Important properties:

* **trkpt_idx** of first **rtept** in **trkseg** is 0. So, if there are two **trkseg**s, there will be two **rtept**s with **trkpt_idx** = 0
* **trkpt_idx** of last **rtept** in **trkseg** is equal to number of **trkpt**s in **trkseg** minus 1. For example, if **trkseg** has 12 **trkpt**s, **trkpt_idx** of last **rtept** should be 11
* Neighbouring route **segments** of are overlapping: the end of previous **segment** and start of next **segment** is the one and same **trkpt**.
* There is exception when neighbouring route **segments** don't overlap (don't share the same **trkpt**). It happens when there is **rtept** "between" route **segment**s. End of previous route **segment** is one **trkpt**, and start of next route **segment** is another **rtept**. But these two **trkpt**s are totally equal by lat, lon and other params.
* Route **segment** overlapping can be detected via **length** and **startTrkptIdx** (the latter is used only for convenience of human reading):
  - If sum of **startTrkptIdx** and **length** of prevous route **segment** equals **startTrkptIdx** of next route **segment**, route **segment**s are not overlapping
  - If sum is less by one, then route **segment**s are overlapping
* There can be straight route **segment**s. They are marked with **id="-1"**. They can appear in two cases:
  - It is multiprofile route, and user selected straight line
  - User placed **rtept** too far away from closest road, so osmand made straight line between **rtept** and road
* trkpts = length - (segments - 1) + (rtepts - 2), where:
  - trkpts - amount of **trkpt**s inside **trkseg**
  - length - sum of all **length**s of route **segment**s inside **trkseg**
  - segments - amount of route **segment**s inside **trkseg**
  - rtepts - amount of **rtept**s owned by **trkseg**  

#### Example:

```xml
<gpx version="1.1" creator="OsmAndRouterV2" xmlns="http://www.topografix.com/GPX/1/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.topografix.com/GPX/1/1 http://www.topografix.com/GPX/1/1/gpx.xsd">
  <metadata>
    <name>Fri 06 Nov 2020</name>
  </metadata>
  <trk>
    <name>Fri 06 Nov 2020</name>
    <trkseg>
      <trkpt lat="52.3639849" lon="4.8900533">
        <ele>0.801</ele>
      </trkpt>
      <trkpt lat="52.3636917" lon="4.8922849">
        <ele>0.998</ele>
      </trkpt>
      <trkpt lat="52.3636885" lon="4.892309">
        <ele>1</ele>
      </trkpt>
      <trkpt lat="52.3636426" lon="4.8922902">
        <ele>0.963</ele>
      </trkpt>
      <trkpt lat="52.363564" lon="4.8922607">
        <ele>0.899</ele>
      </trkpt>

      ....

      <extensions>
        <route>
          <segment id="7372058" length="3" segmentTime="178.44" speed="1.11" turnType="C" types="0,1,2,3,4,5,6" names="57" />
          <segment id="334164679" length="5" segmentTime="86.11" speed="1.11" turnType="TR" turnAngle="91.88" types="7,8,0,9,10,11,12,13,6" pointTypes=";;14,15;16,17,18;" names="58" />
          <segment id="334603581" length="6" segmentTime="75.5" speed="1.11" types="19,20,21,7,8,0,22,9,10,11,12,13,23,6" pointTypes=";14;16,24;16,24;14;" names="58" />
          <segment id="446707354" length="3" segmentTime="8.32" speed="1.11" turnType="TSLL" turnAngle="-25.44" types="19,25,21,7,8,22,9,1,11,12,13,6" names="58" />
          ...
        </route>
        <types>
          <type t="lit" v="yes" />
          <type t="oneway" v="yes" />
          <type t="highway" v="unclassified" />
          <type t="surface" v="paving_stones" />
          <type t="maxspeed" v="30" />
          ...
        </types>
      </extensions>
    </trkseg>
  </trk>

  <rte>
    <rtept lat="52.3639945" lon="4.8900532">
      <extensions>
        <profile>pedestrian</profile>
        <trkpt_idx>0</trkpt_idx>
      </extensions>
    </rtept>
    <rtept lat="52.3612797" lon="4.8911677">
      <extensions>
        <profile>pedestrian</profile>
        <trkpt_idx>24</trkpt_idx>
      </extensions>
    </rtept>
    <rtept lat="52.356996" lon="4.8912071">
      <extensions>
        <profile>pedestrian</profile>
        <trkpt_idx>89</trkpt_idx>
      </extensions>
    </rtept>
    <rtept lat="52.3542374" lon="4.8947024">
      <extensions>
        <profile>pedestrian</profile>
        <trkpt_idx>121</trkpt_idx>
      </extensions>
    </rtept>
  </rte>
</gpx>
```

## Tags name for sensor data

Increased compatibility of OsmAnd tracks with **Strava and Garmin Basecamp**. *Temperature, Heart Rate, Bicycle Power, Bicycle Cadence, and Bicycle Speed* sensors are enrolled in the Garmin https://www8.garmin.com/xmlschemas/TrackPointExtensionv1.xsd extension scheme.

```xml
<extensions>
    <gpxtpx:TrackPointExtension>
        <gpxtpx:hr>107</gpxtpx:hr>
        <gpxtpx:wtemp>107</gpxtpx:wtemp>
        <gpxtpx:cad>107</gpxtpx:cad>
    </gpxtpx:TrackPointExtension>
</extensions>
```

## GPX Collection in OsmAnd Binary Format (OBF)

It's possible to convert multiple GPX files into OsmAnd Maps (.obf), so this collection could contain thousands GPX tracks and work flawlessly. 
Specific features such as special icons on the map, track lines appearance, search functionality are supported via GPX extensions tags.

### Map line display

Example (to do).
To be supported: color could be defined on trkseg, trk, metadata.

```xml
<trk>
  <extensions>
    <osmand:color></<osmand:color>
  </extensions>
</trk>
```

|Name|OBF name| Spec and Purpose|
|:--------|:---------------|:---------------|
| color | color | Color track is converted to predefined list (link) of colors | 
| osmand:width | gpx_width | Width track to be displayed (converted to thin/thick/bold/medium), by default medium if not parsed | 
| shield_bg, shield_fg, shield_fg2, shield_text, shield_textcolor  | - | Displays shields similar to OSMC (link) symbols in OsmAnd  | 
| osmand:use_osmc_colors | use_osmc_colors | Now modifies color, width - displays transparent colors and different width. To be replaced with color / width? |

### Map waypoints display

Example
```xml
<extensions>
    <gpxtpx:TrackPointExtension>
        <gpxtpx:hr>107</gpxtpx:hr>
        <gpxtpx:wtemp>107</gpxtpx:wtemp>
        <gpxtpx:cad>107</gpxtpx:cad>
    </gpxtpx:TrackPointExtension>
</extensions>
```
- ...

### General Track Info

|Name|OBF name| Spec and Purpose|
|:--------|:---------------|:---------------|
| ele, lat, lon | Map section: ele_graph, start_ele. POI calculated: uphill, downhill, distance, max_ele, min_ele, start_ele, finish_ele  | To restore inforrmation about altitude |
| speed, lat, lon | POI calculated: avg_speed, ...  | To restore general information about speed |


### Tracks Search

Use route_id vs osm_id. Suggestion: differentiate OSM objects and other objects by prefix "OSM-...".

- ...

### Waypoints Search

- ...

### Route Context menu

- Description (POI section)
- Custom extension tags are not supported yet (POI section)


### Waypoint Context menu

- Description (POI section)
- Custom extension tags are not supported yet (POI section)
