---
title: Curation workflow
permalink: wiki/Curation_workflow
layout: wiki
---

### Processing new publications

1.  Add reference info to the Phenoscape II Curation Log in Googledocs.
    Use the log to keep track of curation status for publications
    (what’s been done by who and when).
2.  Add citation to the Phenoscape Endnote file
    (Phenoscape_pubs_A_papers.enl in Dropbox)
    1.  Create PSPUB identifier (ask Jim or Wasila for explanation)
    2.  In Phenex file for the paper, record the PSPUB identifier in the
        Dataset Tab’s Publication field
3.  Upload PDF of paper to the Mendeley Vertebrate Curation Group
4.  Add Phenex file to DropBox
5.  Make sure you are using Phenex version 1.2 or later, which has the
    autosave feature and will automatically save to files in DropBox -
    no need for SVN or ZigVersion!
6.  Fill in curatorial information in the **Dataset tab**

- - This space is used to record general information about dataset that
    a user should know. Generally, this includes notes on how the data
    was modified from the publication. For example,
  - matrix created from free text descriptions in the publication text
  - only fin or limb characters curated to date
  - additional taxa were added to the matrix
  - coding was updated based on author feedback
  - characters X, Y, and Z were omitted based on character reassessment
    in subsequent publications.
  - evidence code for matrix is IVS

<!-- -->

- - if curator corresponds with author, make note of data of
    correspondence and name of author (e.g., Information recorded here
    consists of modifications made to published data based on author
    communication, 10/12/2013).
  - note if matrix is not published wth paper, then the curator should
    indicate where the dataset came from and where it is available from.
    Please check with Phenoscape as to where they would like the data
    deposited.

Phenex and Mesquite files locations in DropBox: These files are located
in the “Phenoscape-data” folder within DropBox “incomplete-files” folder
contains the working Mesquite (.nex) and Phenex (.xml) files before they
are uploaded to the KB Paul and Nizar’s files are in the “Sereno” folder

### Work Study instructions for creating matrices using Mesquite and Phenex

1\. Gather archosaur publications (with matrices) for curation Add
citation to Phenoscape II Curation Log in Google Docs Add citation and
abstract info to Endote file “Phenoscape_pubs_full_list.enl” located in
the “Publications” folder (in the “Data” folder in DropBox). Once the
paper is ready to load to KB, move this publication citation to
“Phenoscape_pubs_A_list.enl”. Italicize species names in title and
abstract \[work study student\] Create PSPUB identifier for publication.
Ask Jim or Wasila how to do this. Add PDFs to Mendeley obtain PDF online
or, if not available, scan a hardcopy and create OCR using Adobe Acrobat
\[work study student\]

2\. Create matrix files for all pubs \[Much of this work to be done by
work study students!\] Ask authors for electronic versions of matrices
or have work study student manually put matrix into Mesquite
(intermediate steps involving copy/paste into Excel or Text Wrangler)
Manual entry of matrix by student from PDF: Copy and paste matrix from
PDF to Word; replace polymorphisms with “?” because Phenex doesn’t
handle polymorphism yet make sure all taxa are listed to the right (?),
and that character states are in a single continuous line for each taxon
Find/replace each state with a state + space (e.g., find “0” and replace
with “0 “ copy/paste matrix to Excel Click on “text to columns”, then
click “delimited”, click on “space” delimiters, and finish! Open the
space delimited file in Mesquite. Determine if matrix contains higher
level taxa and expand matrix (if needed) for actual species examined (do
this step in Mesquite because it can’t be done easily in Phenex) Copy
and paste character and state free text, taxa from matrix \[work study
student\] Save matrix in Mesquite in NEXUS (.nex) format and import into
Phenex; save Phenex file (NEXml format, .xml) Save the file in
“incomplete-files” folder (“Sereno” folder) in Dropbox

3\. Import the matrix file (.nex) into Phenex Go to File\>Import. Verify
that characters, states, taxa, and matrix have been imported Save the
file to “incomplete_files” folder (“Sereno” folder) and change file
extension to “.xml” Note: ask Jim for help if the import doesn’t work.
You probably need to a space between a taxon name and matrix if there
isn’t one for any taxon

4\. Taxon list update in Phenex see notes on wiki:
<http://phenoscape.org/wiki/Update_Taxon_Lists> Taxon list update -
choose VTO taxon; not sure about the rest of workflow; will it involve
requesting taxa from PaleoDB? Could be done by work study student; They
will leave Valid Taxon blank where there is no exact match to VTO term.

Proofreading \[by workstudy student\] - matrices \[OCR mistakes, student
transcription mistakes\] - character/state free text for OCR mistakes

### Phenex Ontology Configuration

(full details here:
<http://phenoscape.org/wiki/Phenex#Ontology_configuration>) Phenex comes
pre-configured with the ontologies used for Phenoscape, but may need to
be configured to load specific anatomy ontologies (e.g., AMAO or AAO),
and taxonomies. Here’s how to specify which ontologies should be made
available in data entry fields in Phenex. Term sources

To edit the list of terms sources, open the Ontology Sources panel by
selecting View \> Config \> Ontology Sources from the menu. Add a new
source by pressing the '+' button. Enter an HTTP or local file URL in
the URL column, and an optional label of your choice in the Label
column. Press "Apply" to save your list of ontology sources. You will
need to relaunch Phenex in order for it to download the given files and
load all the terms into its ontology session. Creating term filters

The set of terms available in a given entry field are determined by term
filters. Term filters are just saved search specifications which can be
created using the Search Panel.

Create a term filter by opening the Search Panel from View \> Ontology
\> Search Panel. For the Entity field, an example filter is shown below.
Make sure to correctly specify “matches all” vs. “matches any” for the
main and subqueries.

Hit the save button, and save the filter (name it “entities.xml) to the
following location: user \> Library \> Application Support \> Phenex \>
Filters

Note: this folder is hidden on Mac OSX. Should you need to access it
using Finder, first make the folder visible by going to Finder\> Go \>
Go to Folder, and typing in "~/Library"
