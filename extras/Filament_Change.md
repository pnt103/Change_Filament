---
layout: plugin

id: Filament_Change
title: Filament_Change
description: Facilitates changing filament (backs out old, loads new)
author: Pete Turnbull
license: bsd-3-clause

date: 2023-10-06

homepage: https://github.com/pnt103/Filament_Change
source: https://github.com/pnt103/Filament_Change
archive: https://github.com/pnt103/Filament_Change/archive/master.zip

tags:
- filament

screenshots:
- url: /assets/img/plugins/Filament_Change/cf_buttons.png
  alt: Filament Change Buttons
  caption: Filament Change Buttons
- url: /assets/img/plugins/Filament_Change/cf_settings.png
  alt: Filament Change Settings
  caption: Filament Change Settings

featuredimage: /assets/img/plugins/Filament_Change/cf_buttons.png

---

This plugin makes it simple to change filament.

The plugin mimics the actions taken by the change filament action built into
Marlin. That feature is not available on all printers and also requires using
the control box to use, instead of doing everything in OctoPrint.

When Marlin unloads filament using the Advanced Pause (M600) feature, it first retracts
and then pauses to cool the filament slightly, then de-retracts a little less
before it unloads the filament. This is to help prevent pulling a string away 
from inside the nozzle and leaving it in the heatbreak or on the end of the
filament which would make it more difficult to re-load.

Configuration:

* **Unload Length**: Length of filament to reverse extrude when unloading, in mm.
* **Unload Speed**: How fast to unload the filament, in mm/m.
* **Retract Length**: Length of filament to retract before unload, in mm.
* **Retract Speed**: How fast to retract the filament before unload, in mm/m.
* **Retract/Deretract Pause**: How long to cool the filament between retract and deretract when unloading, in seconds.
* **Deretract Length**: Length of filament to deretract before unload, in mm.
* **Load Length**: Length of filament to extrude when loading, in mm.
* **Load Speed**: How fast to extrude when loading filament, in mm/m.
* **Purge Length**: length of purge/re-prime, in mm.
* **Purge Speed**: How fast to extrude when purging filament, in mm/m.
* **Pause Before Park**: Send M0 to pause Octoprint before parking.
* **Retract Before Park**: Perform a small retract before parking.
* **Home Before Park**: Home X/Y before moving to the X/Y parking position.
* **Y Park**: Position on the Y axis where the head will be moved when loading or unloading.
* **X Park**: Position on the X axis where the head will be moved when loading or unloading. Depending on the filament path, may be best set to the midpoint of the X axis.
* **Z Lift Relative**: How high to move the Z axis before unloading, in mm.
* **Park Speed**: How fast to move the head when parking, in mm/m.
