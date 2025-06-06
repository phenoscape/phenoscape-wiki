---
title: Adding Taxa to PaleoDB
permalink: wiki/Adding_Taxa_to_PaleoDB
layout: wiki
tags:
 - Taxonomy
 - Curation
---

# Introduction

This page discusses the procedure for adding taxa to the PaleoDB (aka
PBDB) via the web interface. It is mostly meant as a reference as you
should have received training from the authorized person supervising
your data entry. Note, as mentioned below, that names entered into the
PaleDB do not automatically appear in the Vertebrate Taxonomy Ontology
(VTO), instead you will need to request an update be made to the VTO,
either as a tracker request, or directly to the taxonomy curator.

# Adding taxon names

1.  Go to [paleodb.org](http://paleodb.org)
2.  Login (link at the upper right corner of the startup window). If you
    are not registered as a contributor, you should specify your
    supervisor (e.g., Paula or Wasila) as the authorizer, and your name
    (lastname, first initial, followed by period e.g., Midford, P.) as
    enterer. This will take you to the Main Menu.
3.  The first step is to double check that the taxon is not in PaleoDB.
    Every (chordate) taxon in PaleoDB should be in VTO, but there may be
    a few that have been added since the last time the VTO was updated
    from the PaleoDB. In the ‘Data entry’ column under the heading
    ‘Basic steps’, click the ‘Add/edit taxon name’ link. This will take
    you to a page called ‘Enter the taxon’s full name’. Enter the name
    in the Taxon name field (e.g., *Loganellia scotica*) and click
    Search.
    - If a match is found, then we don’t need to worry about it and when
      we add PBDB to the VTO the name should appear in Phenex. If the
      name is already in PBDB, then we don't need to worry unless the
      containing taxa are not listed in PBDB. If there are no containing
      taxa, the VTO update process will attach taxon directly under
      chordata (which is the default root in our VTO build scripts).
    - If a match is not found, then the Reference search page will
      appear. The reference to search for is the paper that you are
      curating (not the publication where the taxon was originally
      described!) You can search by simply entering the author and PBDB
      to make sure the reference isn’t already there. You don’t need to
      specify year or title in the search, but if the author has lots of
      publications already in the database, adding one of this will
      shorten the list of returned results. Click Search. The resulting
      page will display a list of matches.
4.  If there is no match for the publication, click on the ‘Main menu’
    item in the upper left. To record a new reference, click the ‘Add
    new reference’ in the ‘Basic steps’ area. This will take you to a
    Duplicate reference search page. Enter the name as on the Reference
    search page and hit the ‘Search’ button. When the list of references
    add, click the ‘Add’ button (since the reference shouldn’t be in
    this list). This will take you to the ‘New reference form’ page.
5.  Fill out the form. Enter the first author last name and initials -
    the format requires periods and spaces between the initials. Enter
    the second author in the same way. Additional authors with or
    without initials. Don’t put ‘and’ before the final author’s name.
    Project code can be left blank. Pay careful attention to the
    “Taxonomy” drop down (most will be ‘stated with evidence’ or ‘stated
    without evidence’). For most phylogenetic studies, the correct
    choice will be ‘stated with evidence.’ There are two links to pop-up
    tip sheets that explain how the PBDB administrators expect data to
    be entered.
6.  Once you hit the submit button, it will take you to a page that
    summarizes the reference you added. Now you can add the taxon name.
    There is a link to ‘Add or edit all the taxon names’. Click that
    link and a popup page called ‘Enter the taxon’s full name’ will
    appear. Search again for the taxonomic name you want to enter. If
    the taxonomic name is not in PaleoDB, you should search for and
    record the name with the highest taxonomic rank (e.g., if species
    you are entering does have its family entered yet, start with the
    family, then the genus, then the species). Clicking search will take
    you to a page titled ‘Authority data for \[taxon name\].’
7.  The first step is to specify (with the radio buttons) whether the
    taxon was named in the data record’s primary reference or in an
    earlier publication. For example, the taxon *Loganellia scotica* was
    referenced in Wilson and Mars (2004), but was originally described
    and named in Traquair 1898. In this case the second radio button is
    the appropriate choice. At a minimum, the original author and year
    should be entered. You must also specify whether this taxon is
    extant (living). Additional information, such as ‘type specimen’,
    preservation category, type locality, etc. are optional and not
    recorded for Phenoscape taxa. Then you will reach a page that
    indicates that your taxon has been entered in the database.

# Adding published taxonomic opinions

Next you’ll enter the taxonomic opinion on the parent of the taxon.

1.  Click on Add this author’s taxonomic opinion. Usually, it will be
    repeated from the original description. It will look up the parent
    taxa after you press submit.

# Adding unpublished opinions

1.  Go to the "Add reference" form.
2.  Add the author(s) name in the author fields, the current year in the
    year field, and a proxy title such as "Personal communication
    regarding placoderm taxonomy."
3.  Select "unpublished" as the publication type (there's no "personal
    communication" category because that would be splitting hairs).
4.  Select "stated with evidence" as the "taxonomy" value. Otherwise,
    the opinions would be trumped by earlier-published "with evidence"
    opinions.
5.  Don't worry about the serial name, volume, issue number, first page,
    or last page. These fields are actually optional.
