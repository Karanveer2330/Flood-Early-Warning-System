# Flood-Early-Warning-System

Flood Detection Using Sentinel-1 SAR Imagery in Google Earth Engine
This script detects and maps flood-affected areas using Sentinel-1 SAR imagery in Google Earth Engine (GEE). The workflow is tailored for Ludhiana district but can be adapted for other regions.

Steps to Use the Script

1.Open Google Earth Engine Code Editor

2.Go to the Google Earth Engine Code Editor.

3.Import Required Libraries and Datasets

The script uses the following Earth Engine datasets:

Administrative boundaries: 'FAO/GAUL_SIMPLIFIED_500m/2015/level2'
HydroSHEDS DEM: 'WWF/HydroSHEDS/03VFDEM'
Global Surface Water: 'JRC/GSW1_3/GlobalSurfaceWater'
Sentinel-1 SAR: 'COPERNICUS/S1_GRD'

Set Parameters
Area of Interest (AOI):
Update the district name in this line to your target location:
var Ludhiana = admin2.filter(ee.Filter.eq('ADM2_NAME', 'Ludhiana'));

Date Ranges:
Specify the time periods before and after the flood event:
var beforeStart = '2023-04-15';
var beforeEnd = '2023-06-10';
var afterStart = '2023-06-10';
var afterEnd = '2023-07-23';
Change these dates to match your flood event.

Flood Detection Threshold:
Adjust the threshold for flood detection if needed:
var diffThreshold = 1.25;
Lower values may detect more water, higher values are stricter.

Slope Masking:
To exclude steep areas, set the slope threshold:
var slopeThreshold = 5;
Connected Pixel Threshold:

To remove isolated pixels, set:
var connectedPixelThreshold = 8;
Run the Script

Copy and paste the entire code into the GEE Code Editor.

Click "Run" to execute.

View and Export Results

The script will visualize:
Pre- and post-flood SAR images (raw and filtered)

Initial and final flood extents
The total area of the district and flooded area (in km²) will be printed in the Console.

![image](https://github.com/user-attachments/assets/889f6741-c51b-461b-b0a4-5675f1711d42)

Key Functions in the Script
toNatural(img): Converts dB to natural units.
toDB(img): Converts natural units to dB.
RefinedLee(img): Applies the Refined Lee speckle filter to reduce SAR noise.
