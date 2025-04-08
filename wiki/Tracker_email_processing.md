---
title: Tracker email processing
permalink: wiki/Tracker_email_processing
layout: wiki
tags:
 - Informatics
---

The default update emails from the ontology trackers are cluttered and
confusing for novice users. Since we prefer discussion of new ontology
terms to take place on the mailing lists, it is best that readers of the
update emails do not follow the embedded links and post their comments
directly to the tracker. Also, both the "from" and "to" addresses on
these emails go to a noreply address at Sourceforge, making it difficult
to keep replies to proposals of new terms on the mailing list.

Thus, update emails from the [teleost
anatomy](http://sourceforge.net/tracker/?group_id=76834&atid=994764) and
[zebrafish
anatomy](http://sourceforge.net/tracker/?group_id=76834&atid=994726)
Sourceforge trackers are sent to an email address at NESCent. Messages
to this email address are automatically piped to
<a href="Media:format_tracker_mail.txt" class="wikilink"
title="a script">a script</a>, which replaces the "from" header with an
address which is allowed to post on the teleost-discuss mailing list.
The "to" and "reply-to" headers are given the address of the mailing
list, obo-teleost-discuss@lists.sourceforge.net. The script extracts
relevant information from the update emails and reformats it in a more
user-friendly message. Users can reply directly to the message and
continue discussion of term proposals on the mailing list.

The NESCent mail server runs the script with
<a href="WG:tracker_command_line" class="wikilink"
title="this command line">this command line</a>.
