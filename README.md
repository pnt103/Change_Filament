# Change_Filament

This plugin makes it simple to change filament.

The plugin mimics the actions taken by the change filament action built into
Marlin. That feature (Advanced Pause) is not available on all printers and also
requires using the control box to use, instead of doing everything in OctoPrint.
This version does not (yet) mimic Marlin's retract/pause/deretract before unloading,
but it does allow for an additional purge if needed to clear the previous filament
or fully prime the nozzle.

## Setup

Install via the bundled [Plugin Manager](https://github.com/foosel/OctoPrint/wiki/Plugin:-Plugin-Manager)
or manually using this URL:

    https://github.com/pnt103/Change_Filament/archive/master.zip

## Use

Set the configuration as described below, then refresh the page.

To use:

* Change to the Control tab
* Click **Park** to park the nozzle in a convenient location for reloading
* Change to the Temperature tab
* Preheat nozzle to old filament temperature
* Change to the Control tab
* Click **Unload** to unload the old filament
* Feed in the new filament
* If the new filament requires a different temperature, preheat the nozzle to the new temperature
* Click **Load** to load the new filament, which will feed new filament to the nozzle
* Optionally, **Purge** more filament to clear any old filament or reprime the nozzle
* Done! Start printing, or cool down the nozzle to finish

The M600 button can trigger the built-in Change Filament function on certain builds of Marlin. This procedure must be completed using the control box.

M600 in Marlin, and the associated M702 command, perform a fairly large retraction
followed by a short pause to cool the filament slightly and then a de-retraction to compress it,
to improve unloading, before withdrawing the filament the rest of the way.  Not implemented in
the "Unload" command here yet.

## Configuration

* **Unload Length**: Length of filament to reverse extrude when unloading, in mm.
* **Unload Speed**: How fast to unload the filament, in mm/m.
* **Retract Length**: Length to retract before unloading, typically 12-18mm.
* **Retract Speed**: How fast to retract the filament before unloading, in mm/m.
* **Retract/Deretract Pause**: How long to cool the filament between retract/deretract when unloading, in seconds.
* **Deretract Length**: Length of filament to deretract before unloading, typically half the retract length.
* **Load Length**: Length of filament to extrude when loading, in mm.
* **Load Speed**: How fast to extrude when loading filament, in mm/m.
* **Purge Length**: length of purge/re-prime, in mm.
* **Purge Speed**: How fast to extrude when purging filament, in mm/m.
* **Y Park**: Position on the Y axis where the head will be moved when loading or unloading.
* **X Park**: Position on the X axis where the head will be moved when loading or unloading. Depending on the filament path, may be best set to the midpoint of the X axis.
* **Z Lift Relative**: How high to move the Z axis before unloading, in mm.
* **Park Speed**: How fast to move the head when parking, in mm/m.

## Suggested Configurations

### CR-10S

Most of the default values work well for CR-10S and probably for other printers in that line, but manually set the X park to 150.

### Monoprice Select Mini v2

Default values work well, set X park to 100-120 so the bowden tube has less of a bend when parked.
