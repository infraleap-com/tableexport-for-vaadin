# TableExport Add-on for Vaadin 8

TableExport is a Data Component add-on for Vaadin 8.
Legacy versions of the add-on that worked with Vaadin 7 (< 1.8.0) and Vaadin 6 (< 1.3.0) should still be available on the Vaadin.com site.

## About this fork

Version 1.8.0 is the version that a fork by Rijad Zuzo ([Tebra/tableexport-for-vaadin](https://github.com/Tebra/tableexport-for-vaadin),
July 2018) built on top of the last release of [jnash67/tableexport-for-vaadin](https://github.com/jnash67/tableexport-for-vaadin):
compared to the original it exports the presented value when a column has a presentation provider, formats
`LocalDate` and `LocalDateTime` cells, aligns cells by their presented value and handles `null` cell values and
columns without an id. It is published unchanged (Java package `com.vaadin.addon.tableexport`, tag `1.8.0`).

Version 1.8.1 fixes three bugs of 1.8.0 and moves the add-on to its own Java package:

* The type of a cell is the class of the value it shows (1.8.0: the class of the column's value provider, so numbers
  were written as text with the default style).
* The totals row works for grids (1.8.0 ended in a ClassCastException and summed nothing).
* A `java.util.Date` cell keeps its date (1.8.0 overwrote it with its text).
* Java package `com.infraleap.tableexport`: users of 1.8.0 change their imports, nothing else.

Maven coordinates: `org.vaadin.addons.infraleap:tableexport-for-vaadin`. Version 2.0.x (branch `2.0`) is the port to
Vaadin Flow.

## Overview
* Exporting data to Excel or CSV formats is a common task that comes up time and again. The solution can figured out from various forum posts but it takes a while to put everything together, especially the writing of the Excel file to the browser.
* This add-on takes a Grid or Table as input and exports a decent Excel file containing the data in the Container. It also handles HierarchicalDataProviders / HierarchicalContainers and the resulting Excel file will have the categories and subcategories properly grouped/outlined.
* There are a number of configurable properties. The user can specify a worksheet name, a report title, and an output file name. The user can also specify if there should be a Totals row at the bottom of the export. The user can pass in custom POI CellStyles. However, if none of these are specified, the user only needs to pass in a Grid/Table.
* This add-on requires the Apache POI library (http://poi.apache.org/). 
* This add-on uses Charles Anthony's solution from: http://vaadin.com/forum/-/message_boards/view_message/159583

## Building and running demo

* git clone <url of the github repository>
* mvn clean install
* cd tableexport-demo
* mvn jetty:run

## License

Add-on is distributed under Apache License 2.0. For license terms, see LICENSE.txt.
