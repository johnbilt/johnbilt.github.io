---
layout: page
title: Working with TAMS
subtitle: Time Based Metadata
hero_image: /images/resources_background.png
show_sidebar: false
menubar: resources_menu
---

The design of TAMS lends itself very well to AI analysis of content, stored in small Segments.  As Segments arrive in the store, it is possible to use the webhook event notifications to trigger the content to be analysed.  Equally, most live workflows have additional feeds of metadata alongside the media, whether this is created through manual logging processes or through data feeds such as sports data.  

[App Note 0004](https://github.com/bbc/tams/blob/main/docs/appnotes/0004-tams-for-data.md){:target="_blank"} on the [TAMS spec Github](https://github.com/bbc/tams){:target="_blank"} provides some more detail on the different types non-media files and when they could or could not be a good fit to store within a TAMS store.   This document focuses on the question of where to store the time-based metadata that is generated, and whether this should be stored within TAMS?

At the core, TAMS is designed to hold media and allow the discovery of all the media elements that make up a piece of content.  The store does have a Flow type for storing data files against a timerange.  This means that it is possible to take the file from an AI analysis processes or the output from a logging stage and then upload that as a Segment against a Flow.  While this is a perfectly legitimate use for the TAMS store it will not give the user the ability to use the data for activities like searching content.

### Time Addressable metaData Store

The Time Addressable metaData Store (TADS) is a concept for how time based metadata should be stored in a way that is optimised for working with a Time Addressable Media Store (TAMS).

The TADS approach assumes that the TAMS store is part of a wider architecture.  The TADS element could either be a separate microservice or integrated into a larger component such as a MAM system.

TAMS provides both strong identity and timing data for media content.  For the TADS to work with it efficiently, this timing and identity information should also be used to store the metadata.  This removes the need for converting back and forth between different identities and timing models when locating media.

Metadata should be stored in the TADS model using the Source and Flow ID’s used within TAMS.  If the live source originates in an NMOS environment then the Source and Flow identities can be preserved between the different domains offering greater interoperability.

Where the metadata is relevant to a particular section of the content, the timerange format from TAMS should be used.  This preserves the timing data in a consistent format between the two components.

If the source metadata is provided with a different timing data model then it is recommended to convert to the same code timing model used in TAMS which is based on International Atomic Time (TAI)

### Working with TADS and TAMS

To locate content in TAMS using the time based metadata it is expected that a user would start the process in some form of UI presentation layer, most likely a MAM or PAM system.  This would provide the user with an interface to be able search for content.

The presentation layer would forward the search request to the TADS service which could then search through the time based metadata.  It would then return the list of potential Sources that a user might be interested and timeranges.

On selecting the content to be viewed the TADS store could provide more data to populate the presentation layer UI.  For example the time based metadata may be displayed as additional metadata tracks on a UI alongside a player window.

To enable the user to quickly access the right piece of content, the presentation layer could take the Source and timerange metadata from the TADS service.  Using this data it could then query TAMS for the relevant Flows for media playback and then jump directly to the required timerange.

The key to making this process as simple as possible at the point of search is to normalise the data on the way in and the consistency between the different components.

![Sequence diagram showing how TAMS and TADS could fit together](/images/tams_and_tads.png)

### TADS Design

Currently there is no reference architecture or API specification for TADS as there is for TAMS. However, the technical approach is not dissimilar to that already taken by MAM and PAM vendors.  The key different is in the timing and reference data stored in the correct formats.

It is recommended that the TADS component should store the following fields as a minimum:

* Top level Source ID of the required content

* Flow ID if the analysis is specific to a certain flow

* Timerange that the metadata applies to

* Metadata type (or track), for example transcription or logging metadata

* Data to be searched

* Vector embedding (optional)

It is recommended that the data store behind should match the access patterns required.  This means that the same data may potentially be stored in multiple components depending on the access patterns.  An example is transcrption data which may be stored as phrases in a search index, but also in a simple data table with word by word timing for edit by text workflows.
