---
layout: infographic
title: TAMS Data Model
subtitle: Understanding the building blocks
hero_image: /images/resources_background.png
show_sidebar: false
cards:
  - title: Sources
    icon: fa-broadcast-tower
    summary: The logical representation of a piece of content, independent of any particular format or resolution.
    detail: |
      A **Source** represents a piece of content at its most abstract level — it identifies *what* the content is, not how it's stored or encoded.

      **Key points:**
      - Sources are automatically created when you create a Flow — you don't create them directly via the API
      - A Source can have multiple Flows representing different formats of the same content (e.g. HD and UHD versions)
      - Multi-essence Sources collect related mono-essence Sources (e.g. combining a video Source with its audio Source)
      - Sources carry metadata like labels, descriptions and tags that describe the content
      - Source collections are managed automatically by the store when Flow collections are created

      **Example:** A live camera feed is a Source. It might have Flows for 1080p, 4K, and a proxy — all under the same Source identity.

  - title: Flows
    icon: fa-stream
    summary: A specific format or encoding of a Source, holding technical parameters like codec, resolution and sample rate.
    detail: |
      A **Flow** represents a specific technical rendition of a Source. It holds the codec, resolution, frame rate, sample rate and other format-specific parameters.

      **Key points:**
      - Flows are the primary element you create when storing content in TAMS
      - Mono-essence Flows contain a single media type (video only, or audio only)
      - Multi-essence Flows collect mono-essence Flows together to represent a combined programme
      - Each Flow has its own timeline where Segments are registered
      - Creating a Flow with a Source ID will auto-create the Source if it doesn't already exist
      - Technical parameters (codec, resolution, bit depth, sample rate) are stored at the Flow level

      **Example:** A 1080p50 H.264 video flow, a 48kHz PCM audio flow, and a multi-essence flow collecting them together.

  - title: Segments
    icon: fa-puzzle-piece
    summary: A time-ranged portion of a Flow's timeline, pointing to the media Object that contains the actual content.
    detail: |
      A **Segment** maps a time range on a Flow's timeline to a specific media Object in storage. It's the bridge between the logical timeline and the physical media.

      **Key points:**
      - Each Segment has a defined timerange (start and end) on the Flow timeline
      - A Segment references an Object ID — the actual media file in storage
      - The same Object can be referenced by multiple Segments (this is how edit-by-reference works)
      - When re-using an Object, you can specify offsets and partial ranges to use only part of the media
      - Segments are registered against mono-essence Flows only (multi-essence Flows have no direct Segments)
      - Timing metadata in the media file should match the timerange declared during registration

      **Example:** A 10-second chunk of video covering 00:01:30 to 00:01:40 on the Flow timeline, pointing to a media file in object storage.

  - title: Objects
    icon: fa-cube
    summary: The actual media files stored in object storage, accessed via pre-signed URLs from the TAMS API.
    detail: |
      An **Object** is the physical media file — the actual bytes of video, audio or data stored in object storage (e.g. S3).

      **Key points:**
      - Objects are stored in standard object storage and accessed via pre-signed URLs
      - The TAMS API provides pre-signed URLs for upload — no separate storage credentials needed
      - After uploading, you register the Object against a Flow by creating a Segment
      - Objects can be shared across multiple Flows and Segments (the basis of edit-by-reference)
      - The store tracks Object re-use automatically
      - Objects are typically short media chunks (seconds to minutes) rather than entire programmes

      **Example:** A .ts file containing 6 seconds of H.264 video, stored in S3 and referenced by one or more Segments.

  - title: Storage
    icon: fa-database
    summary: The underlying object storage layer where media Objects live, abstracted by the TAMS API.
    detail: |
      **Storage** is the underlying persistence layer where media Objects physically reside. TAMS abstracts access to storage through the API.

      **Key points:**
      - TAMS uses standard cloud object storage (e.g. AWS S3) for media persistence
      - The API provides pre-signed URLs so clients upload/download media directly without needing storage credentials
      - Storage is referenced at the Flow level — each Flow has a storage endpoint
      - The store manages the lifecycle of Objects and can track which Objects are still in use
      - Storage backends are implementation-specific — the API is storage-agnostic
      - Media deletion is managed through the API; removing Segments and Flows triggers cleanup of unused Objects

      **Example:** An S3 bucket holding thousands of media chunks, with the TAMS API managing all access control and lifecycle.
---

The TAMS data model is built around five key concepts. Click any card below to learn more about how each element works and how they relate to each other.
