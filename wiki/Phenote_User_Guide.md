---
title: Phenote User Guide
permalink: wiki/Phenote_User_Guide
layout: wiki
tags:
 - Informatics
 - Help
---

This guide covers the use of Phenote specifically for the Phenoscape
configuration. Some more general documentation can also be found at the
[Phenote website](http://www.phenote.org/help.shtml).

## System requirements

Phenote runs on most modern platforms, but requires Java 1.5 (aka Java
5) or later. An appropriate Java is included with Mac OS X 10.4 or newer
(Phenote cannot run on Mac OS X 10.3). For Windows, you can download the
latest Java from <http://www.java.com/>. If you're running Linux, please
consult your system documentation for how to get Java.

## Installation

### Download

Phenote can be downloaded from the [OBO Sourceforge project
site](http://sourceforge.net/project/showfiles.php?group_id=76834&package_id=270424).
There are separate downloads available for Mac and Windows, as well as a
download of the application source code. Download the appropriate zip
file for your platform.

- **Mac:** Double-click the downloaded file to unzip it. You should see
  the application, "Phenote.app". Drag it anywhere you like to install.
  Double-click the application to launch Phenote.
- **Windows:** Double-click the downloaded file. Click on "Extract all
  files" in the resulting window. Use the Extraction Wizard to put the
  Phenote folder wherever you want. Launch Phenote by double-clicking
  "Phenote.bat" inside the Phenote folder. It will take several seconds
  for the Phenote window to appear. *Do not attempt to run Phenote from
  "inside" the zip file - it will not work properly without first
  extracting the files to another folder.*
- **Linux/Unix:** *forthcoming*

### First run

The first time you launch Phenote you will be presented with a window
from which you can choose a configuration. Select "phenoscape" and press
OK. This window can be accessed any time via the *Settings \> Set
Configuration...* menu item. You will also likely be presented with the
ontology update window. Choose "Update All" and continue. Once Phenote
has finished starting up, choose the Phenoscape interface layout via the
*View \> Layouts \> Phenoscape* menu item.

## Using the docking interface

### Docking components

Phenote's interface consists of "docking" components which can be
arranged into any layout the user prefers. A default layout for
Phenoscape can be accessed via the menu item *View \> Layouts \>
Phenoscape*. Each component can be minimized or closed using the
window-like controls in its title tab. Pressing the arrow in a title tab
will pop out a component into its own floating window. Pressing the
arrow in the floating component's title tab will return it to the main
window. Components can be grouped together in tab groups, where only one
of the tabbed components is shown at a time. Click on a title tab to
bring a component to the front. If there is not enough space, all tabs
in a tab group may not be visible. In this case, left and right arrows
will appear in the control tab for that group, which can be used to
cycle through the components. Alternatively the downward pointing arrow
can be used to display a selectable menu of the tabbed components.

### Locking the interface layout

The docking layout can be "locked" so that you don't accidentally
rearrange your components (annoyingly easy to do). Choose the *Settings
\> Lock Docking Components* menu item.

### Displaying specific components

Components that are not currently displayed can be accessed through the
*View \> Show* menu. Components are grouped into functional collection
submenus. Some components can be opened repeatedly to display multiple
instances (e.g. Complete Ontology Tree View), while others will only
display a single instance (e.g. Annotation Editor).

## Working with files

### File names

Phenote can work with only one "project" (set of phenotype annotations)
at a time. You can choose a place to save the current annotations via
the *File \> Save* menu item, or the Save toolbar button. In the Save
dialog, choose the Format "Tab Delimited", and append the extension
".tab" to the end of the filename you enter. *Right now this is the
responsibility of the user; in the future Phenote should take care of
appending this for you.* The Phenoscape configuration saves data for a
project in 3 files; for this reason it is a good idea to create a
separate folder in which to save each project's files. Your phenotype
annotations are saved with the filename you provide. Phenote will also
save a file containing Taxon List entries in the same folder, with
"-taxon-list" appended to the name you gave the main file. When opening
or saving a project in Phenote, just choose the main phenotype
annotations file - the taxon list file will automatically be opened and
saved at the same time. The third file in your project folder is an
optional NEXUS file containing a tree relating your taxa. More
information on this file can be found in the
<a href="#Phylogeny_Chooser" class="wikilink"
title="Phylogeny Chooser">Phylogeny Chooser</a> section.

If you give your annotations file the name "fish_phenotypes.tab", the
following files may be present in your project folder:

- **fish_phenotypes.tab** - this is the main annotations file you choose
  for opening and saving
- **fish_phenotypes-taxon-list.tab** - this file will be automatically
  found by Phenote when you choose your main annotations file
- **fish_phenotypes.tre** - this file can contain a phylogeny of your
  taxa in NEXUS format

### Saving changes

If you have made edits to your current document, but have not yet saved,
you will see an unsaved changes marker in your window titlebar. On the
Mac, this will be a black dot inside the red window close button. On
Windows and other platforms, there will be a bullet character in front
of the window titlebar text. When you save, using the *File \> Save*
menu item, the unsaved changes marker will disappear. If you quit
Phenote without saving, you will be warned that there are unsaved
changes and given the opportunity to save.

## Using Phenote components

### Annotation Editor

The editor component displays a detailed data entry interface for the
currently selected row in one of the table components. It edits the most
recently focused table component. *Sometimes when Phenote is first
launched, no table has yet been focused and the editor displays a blank
canvas - just click on a table to see an editing interface.* The
displayed entry fields correspond to the columns of the focused
annotation table. Most fields are either free text or autocomplete. Free
text fields accept any input, while autocomplete fields will display a
drop-down menu when you begin typing. Autocomplete fields help you to
find, and force you to choose, a valid ontology term. The
<a href="#Term_Info_Browser" class="wikilink"
title="Term Info component">Term Info component</a> will update with
detailed information for each ontology term as you move through the
autocomplete menu.

Some autocomplete fields are configured to choose terms from more than
one ontology. In this case a popup menu in front of the field will allow
you to search within either ALL or just one of the configured
ontologies.

Some autocomplete fields are followed by a "Comp" button. Press this
button to open the post-composition dialog, in which you can create a
more specific ontology term by creating relationships to existing terms
using the
<a href="Guide_to_Character_Annotation#Genus-differentia_definitions"
class="wikilink" title="genus-differentia method">genus-differentia
method</a>.

Two additional types of fields are the list field and the pick list
field. A list field displays an uneditable list of values in its text
box. Edit the values by using the corresponding annotation table (e.g.
the
<a href="#Specimens" class="wikilink" title="Specimens table">Specimens
table</a>). A pick list field is similar to a list field, but its values
are chosen by clicking the "Edit" button next to the field to choose
from values entered into another list field. For example, the
"Voucher(s)" field is configured to pick from values entered into the
"Specimens" list field.

### Term Info Browser

The term info component displays detailed information about ontology
terms as they are selected elsewhere in the interface. You can view the
term's definition, synonyms, relationships to parent and child terms,
and several other properties. Parent and child terms are displayed as
hyperlinks which can be clicked to display information about those terms
in the info component.

### Annotation Table

This is the data table containing the phenotype annotations stored in
your main data file. Add, delete, and duplicate rows (phenotype
annotations) using the toolbar buttons above the table. Select a row to
edit its values in the <a href="#Annotation_Editor" class="wikilink"
title="Annotation Editor component">Annotation Editor component</a>. You
may need to click the title tab of the Annotation Table for the
Annotation Editor to display the appropriate entry fields. You can
select multiple rows in order to enter the same value in a field for
them all simultaneously (bulk editing). Individual values can also be
edited directly in the table by double-clicking the cell. However,
fields containing lists of values cannot be edited within the table.

The rows visible in the table can be filtered using the search field at
the bottom of the panel. The default setting, "Simple Filter", filters
rows based on simple text matching of its input with values in any table
column. You can filter on a particular column by selecting its name
using the popup menu. If the chosen field accepts ontology term values,
the filter input will change to an ontology term autocomplete interface.
You can select how ontology term values are matched using the
Exact/Inherit radio button. The "Inherit" option allows not only exact
matches, but also any values which ontologically inherit from the input
term. For example, using the "Inherit" option, a user can enter a
taxonomic order such as "Siluriformes" and match any rows containing
values that are species within this order.

### Taxon List and Specimens

Both of these tables behave in much the same way as the
<a href="#Annotation_Table" class="wikilink"
title="main annotation table">main annotation table</a>. However, they
also have some specialized features.

#### Taxon List

You can enter the list of taxa described in a publication into the Taxon
List table. You can pick taxa from this table in order to annotate their
phenotypes. Select a taxon by using the checkbox on its row. All the
checked taxa can be copied into the main Annotation Table by pressing
the Generate Characters button in the component's toolbar. The other
extra buttons in the Specimen List toolbar manipulate the checkboxes in
various ways. Since all the copied rows will be selected in the
Annotation Table, you can apply the same phenotype to them all by using
the bulk editing features of the
<a href="#Annotation_Editor" class="wikilink"
title="Annotation Editor component">Annotation Editor component</a>.
Because the values are copied between tables when you use the Generate
Characters function, keep in mind that modifications made to taxon
information in the Taxon List will not be applied to phenotype
annotations already created in the Annotation Table.

#### Specimens

The Specimens table displays the list of specimens entered for the taxon
currently selected in the Taxon List. Unlike other tables, the Specimens
table does not use the <a href="#Annotation_Editor" class="wikilink"
title="Annotation Editor">Annotation Editor</a>; all editing is done
directly in the table. This allows you to work with the Taxon List and
Specimens table simultaneously without repeatedly updating which table
is being modified by the editor component.

### Phylogeny Chooser

The Phylogeny Chooser component can display an evolutionary tree
relating the species in the
<a href="#Taxon_List" class="wikilink" title="Taxon List">Taxon List</a>.
By selecting nodes on the tree, you can select particular taxa in the
Taxon List to use for a phenotype annotation.

#### Inputting a phylogeny

The tree can be input by pasting a
[Newick-format](http://evolution.genetics.washington.edu/phylip/newicktree.html)
phylogeny into the text field at the bottom of the component.
Alternatively, the tree can be obtained from a
<a href="#File_names" class="wikilink"
title="properly-named">properly-named</a> NEXUS file in the same folder
as your main data file. You can manually create this file outside of
Phenote, and then copy it into place with the correct name. More easily,
you can use the "NEX" button in the Phylogeny Chooser toolbar to write
out a default NEXUS file containing an unresolved phylogeny of all taxa
presently entered into your Taxon List. You can then open this file in a
program such as [Mesquite](http://mesquiteproject.org/) or
[MacClade](http://macclade.org/macclade.html) to correct the topology of
the tree. The tree you want to use should be the first stored tree in
the NEXUS file. *If you later add taxa to your taxon list, Phenote
cannot merge them into an existing NEXUS file. You should add them
manually to an existing tree.*

#### Making selections

Drag-select or click nodes on the phylogeny in order to select their
descendant taxa. Individual nodes can be selected or deselected via
control-clicking. Press the "Apply Selection" button (a blue square) in
the Phylogeny Chooser toolbar to select the checkboxes of matching taxa
in the Taxon List. The tree can contain either more or fewer taxa than
are actually present in the Taxon List, but taxon names must exactly
match those in the TTO for the phylogeny to be useful.

### Scratch Lists

The Scratch Lists component lets you create temporary annotation tables
in which you can create template annotations (which you will usually
only partially fill in). These template annotations can be dragged onto
the <a href="#Annotation_Table" class="wikilink"
title="main annotation table">main annotation table</a> to start new
phenotype annotations. Use the toolbar buttons to create and delete
scratch list tables. You can double-click table cells to name a list
anything you want. Select a scratch list name and press the table button
in the Scratch Lists toolbar to display the annotation table for that
list.

If you change the name of a scratch list while its table is open, the
table component's title tab will not update until it is closed and
re-opened. Also, keep in mind that scratch lists are temporary
("scratch") and are not saved with your data file.

### Complete Ontology Tree View

*forthcoming*

#### Usage

The following table describes the entry fields in the PhenoScape
configuration. Phenote does not force you to fill in them all, but see
the table for when to use each field.

<table>
<thead>
<tr>
<th><p>Field</p></th>
<th><p>Usage</p></th>
</tr>
</thead>
<tbody>
<tr>
<td><p>Publication</p></td>
<td><p>the publication describing the character state<br />
CrossRef has a <a
href="http://www.crossref.org/SimpleTextQuery/">free-text query form</a>
for looking up DOIs</p></td>
</tr>
<tr>
<td><p>Taxon</p></td>
<td><p>Genus &amp; species</p></td>
</tr>
<tr>
<td><p>Catalog Number</p></td>
<td><p>museum lot ID</p></td>
</tr>
<tr>
<td><p>Specimen Count</p></td>
<td><p>number of specimens from lot examined</p></td>
</tr>
<tr>
<td><p>Preparation</p></td>
<td><p>type of specimen preparation (skeleton, cleared &amp; stained,
etc.)</p></td>
</tr>
<tr>
<td><p>Entity</p></td>
<td><p>term from anatomy ontology (currently using zebrafish)</p></td>
</tr>
<tr>
<td><p>Quality</p></td>
<td><p>term from PATO - should be "value" term, unless you are filling
in an absolute measurement (e.g. "length")</p></td>
</tr>
<tr>
<td><p>Related Entity</p></td>
<td><p>term from anatomy ontology - only use if the Quality term
descends from "relational quality of continuant"</p></td>
</tr>
<tr>
<td><p>Measurement</p></td>
<td><p>absolute measurement - useful as value for terms such as
"length"</p></td>
</tr>
<tr>
<td><p>Unit</p></td>
<td><p>unit of measurement, if Numerical Value is filled in</p></td>
</tr>
<tr>
<td><p>Compare To</p></td>
<td><p>a taxon to which this phenotype is in comparison to
(optional)</p></td>
</tr>
<tr>
<td><p>Textual Description</p></td>
<td><p>textual description of character state in publication</p></td>
</tr>
<tr>
<td><p>Image URI</p></td>
<td><p>web link to an image, if available</p></td>
</tr>
</tbody>
</table>

Please report any issues you come across by using the [Phenote
tracker](https://sourceforge.net/tracker/?group_id=76834&atid=887913).

## Troubleshooting problems

### Accessing Phenote configuration and logs

The Phenote settings folder contains your chosen configuration, cached
ontology files, interface layouts, and log files. Its location is
platform-dependent:

- **Mac/Linux/Unix:** A folder named ".phenote" within your user home
  directory. Because its name begins with a ".", this folder is
  typically invisible and must be accessed via the terminal interface.
  You can view this folder in the Mac Finder by selecting the *Go \> Go
  to Folder...* menu item, and entering "~/.phenote".
- **Windows:** A folder named ".phenote" in "C:\Documents and
  Settings\\*<your user name>*". If you are the only user on your
  machine, your user name may be "Administrator".

If you are having problems, you may want to look at the contents of the
file "phenote_log4j.log", found in the "log" folder within the Phenote
settings folder. A Phenote developer can examine this file for the cause
of errors you may be experiencing.

### Known issues

- There is a serious problem with Undo for delete actions in tables.
  Using Undo will cause some existing rows to be displayed twice in the
  table. Avoid Undo for now.
- Phenote will not launch without a live internet connection. This is a
  bug in the ontology updating feature.
- Phenote will not launch if it attempts to load an ontology which
  contains a file error. This is a bug in Phenote's ontology loading
  code. If an ontology maintainer posts a faulty ontology to the web
  repository, Phenote will fail the next time it updates that ontology.
  Report the error to the maintainer of the broken ontology.
- The Phenoscape interface layout will not be a choice in the *View \>
  Layouts* menu if you ran an earlier version of Phenote before this
  feature was included. This is a bug in Phenote's layout menu code. If
  you move the "perspectives" folder from within the
  <a href="#Accessing_Phenote_configuration_and_logs" class="wikilink"
  title="Phenote settings folder">Phenote settings folder</a> to the
  Trash, you should see the Phenoscape layout option when you relaunch
  the application.
