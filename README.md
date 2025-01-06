# OctoPrint-Filament_Change

This plugin makes it simpler to change filament.

The plugin can mimic the several of the actions available from the
optional `Advanced Pause`
feature built into advanced versions of Marlin.  
These `Park`, `Unload`, `Load`, `Purge` and `Retract` commands are executed
locally, and do not require special support in Marlin.

Marlin's `Advanced Pause` feature provides the `M600 Filament Change` command
and the associated
`M701 Load Filament` and `M702 Unload Filament` commands
but is an *optional* feature in Marlin, and not available on all printers.
Moreover, those commands normally require using the printer's display control
to use, instead of doing everything in OctoPrint.

This version does not (yet) mimic Marlin's retract/pause/deretract before
unloading, but it does allow for an additional purge after loading, if needed
to clear the previous filament or fully prime the nozzle.  For convenience, it 
also includes a `Retract` button as well as one for `Purge`.

For convenience, this version can be configured to use Marlin's own
`M600 Filament Change` command.  
It does not yet provide a mimic for that, so firmware with the 
`Advanced Pause` feature is required if you wish to change filament
as a single operation.  Use the 
`Park`/`Retract`/`Unload`/`Load`/`Purge`
actions instead..

## Setup

Install manually using this URL:

    https://github.com/pnt103/OctoPrint-Filament_Change/archive/master.zip

## Use

Set the configuration as described below, then refresh the page.

To use:

If you have the
[Consolidated Tabs plugin](https://plugins.octoprint.org/plugins/consolidatedtabs)
or
[Consolidate Temp Control plugin](https://plugins.octoprint.org/plugins/consolidate_temp_control)
from jneiliii, OctoPrint's
**Control** tab (with X/Y/Z/E movement and these Filament Change controls) 
and the **Temperature** tab can be merged.  That will save flipping between them.

* Change to the Control tab
* Click **Park** to park the nozzle in a convenient location for reloading
* Change to the Temperature tab if necessary
* Preheat nozzle to old filament temperature if necessary
* Change to the Control tab
* Click **Unload** to unload the old filament
* If the new filament requires a different temperature, preheat the nozzle to the new temperature
* Feed the new filament into the extruder entry
* Click **Load** to load the new filament, which will feed new filament to the nozzle
* Optionally, **Purge** more filament to clear any old filament or reprime the nozzle
* Done! Start printing, or cool down the nozzle to finish

The M600 button can trigger firmware's built-in Change Filament function on
certain  builds of Marlin and other firmware. This procedure must be completed
using the control box.

`M600` in Marlin, and the associated `M701`/`M702` commands, perform a fairly
large retraction followed by a short pause to cool the filament slightly and
then a de-retraction to compress it and improve unloading, before withdrawing
the filament the rest of the way.  Not implemented in the "Unload" command here
yet.

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

### Creality Ender 3
The default values work well for Ender 3 printers and typically for
other similar printers.  In most cases you can set the X park position  a little
beyond the right edge of the bed, though you will probably need to turn off the
"software endstops" with an `M211` command (if your firmware supports that).
