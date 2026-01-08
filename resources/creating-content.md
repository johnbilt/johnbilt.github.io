---
layout: page
title: Working with TAMS
subtitle: Creating Content in TAMS
hero_image: /images/resources_background.png
show_sidebar: false
menubar: resources_menu
---

When creating content within a TAMS store the sequence of creating the different elements matters. The most important element to create are the Flows.

When creating a Flow, it includes a reference to the Source to which it belongs.  If the Source exists within the store then the two will be linked, however if the Source does not exist then the store will automatically create it.  

When a Source is created the label and description fields from the Flow will initially be replicated to the Source.  It is up to the store implementation whether the tags from the Flow will be replicated to the Source - the AWS open source implementation does but it is optional in the specification.  Once the Source is created it is then possible to call the TAMS API and update the label or description as well as add tags required.

If creating a multi-essence Flow, any mono-essence Flows which are to be collected by it must exist in the store prior to creating the Flow collection. The creation of a multi-essence Flow will cause a multi-essence Source to be created by the store. This new Source will automatically collect any other Sources associated to the Flows collected by the multi-essence Flow.

If new Flows are to be added to an existing multi Flow then they must be created and then added to the collection.  The store in turn will ripple the collections up from the Flow to Source level.

Within the store it is not possible to create Sources directly, these are created and deleted along with their associated Flows.

### Creating New Mono Essence Sources and Flows

To store mono-essence media within TAMS, the first step is to create the separate mono-essence Flows.  These hold the technical characteristics of the segments registered to them.  It is possible to have multiple Flows representing the same content.  For example the video may have multiple different resolutions, bit rates, codecs or frame rates.  Each variant would be stored as a separate Flow, but would be registered with the same Source ID.

On creation of the mono-essence Flows the relevant Source(s) will be automatically created in the TAMS store.  At this point the different media types will still be separate elements.

![Diagram showing the sequence of creating the different elements within the TAMS data model](/images/creation_sequence.png)

To represent the combination of audio and video into a single version, a multi-essence Flow should be created.  This flow has no essence parameters as there is no media stored against it.  The multi-flow definition includes a collection element and this should include the IDs and roles of all Flows to be collected together.

Flow collections can only be created or removed against the multi-flow.  The store will manage the collections automatically, such that querying against a mono-essence Flow will list all the Flows it is collected by, but these cannot be modified against the mono-essence Flow.

On creation of the multi-essence Flow the corresponding multi-essence Source will be created.  Where the Flow collects other Flows then the store will automatically resolve the links to the relevant sources and create the corresponding Source collection links.  The creating system does not need to create the Source collections directly

App Note 007 in the TAMS API repo describes how Source metadata is populated within a store:
[https://github.com/bbc/tams/blob/aaefef3126606a02b73e4c9e24761364a5d5586a/docs/appnotes/0007-populating-source-metadata.md](https://github.com/bbc/tams/blob/aaefef3126606a02b73e4c9e24761364a5d5586a/docs/appnotes/0007-populating-source-metadata.md){:target="_blank"}

### Registering Segments

To simplify the need for both API and storage credentials, the TAMS API will supply pre-signed URLs for media Objects to be uploaded to.  This is done by calling the storage endpoint for a given Flow and requesting the required number of pre-signed URLs.

The creating system then uploads the media Object directly to the object storage using the pre-signed URL.  No other credentials are required for this process.

After upload, the creating system then needs to call the TAMS API and register the Object against the given Flow.  As part of the registration, the creating system will declare the timerange where the Segment sits within the Flow timeline.  For the initial Segment registration the timing metadata within the media file is expected to match the timerange for the Segment.

![Diagram showing the sequence of registering segments with the store](/images/segment_sequence.png)

For [Edit by Reference](edit-by-reference) workflows it is possible to re-use a Segment.  This is done by registering a Segment on the new Flow timeline with the same Object ID as the original Object.  The store will recognise the Object re-use automatically.  At the point of registration it is also possible to specify only part of a Segment to be used and offsets from the internal file timing to that of the Flow timeline.
