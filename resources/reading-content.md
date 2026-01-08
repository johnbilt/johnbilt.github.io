---
layout: page
title: Working with TAMS
subtitle: Reading Content from TAMS
hero_image: /images/resources_background.png
show_sidebar: true
menubar: resources_menu
---

It is expected that a TAMS store will be used as a layer within a larger architecture that would include some form of MAM or PAM.  This would give a user the rich media tools to be able to store and search content.

If locating content directly within a store the usual place to start would be the top level Sources – those which are not collected by any other Source.  It is possible to search on fields including label, description and tags, but these are not expected to replace the rich search of a MAM layer.

Once the required top level Source has been located it is then possible to read down through the data model.  Two routes are possible depending on what is required – either going via the collected Sources or via the multi-essence Flow.

![Diagram showing routes to read through the TAMS data model](/images/read_routes.png)
*Routes to read through the TAMS data model*

The reading system will need to locate the appropriate Flows that match the task that is needs to fulfil.  This may mean reading multiple Flows (eg high quality and proxy video) and then deciding which is most appropriate to use.

Once the Flow has been located it is possible to request the Segments for the whole Flow or just a specific timerange within the Flow.  The store will return the list of Segments along with the timerange that they represent and the URL or URLs to be able to access the content.

Depending on the flags set when requesting content from the store the list of URLs may include pre-signed links or direct paths.  The pre-signed URLs allow direct access to the content on object storage without the need to provision storage credentials directly to the client.  It also ensures permissions are handled within the store meaning that reading systems can only access content they have permission to.

For trusted systems it is possible to provision direct access to the S3 bucket and then read the direct links.  This is only recommended for trusted systems as it will have access to all content stored within the bucket and will not be restricted by any permissions held within the TAMS API.
