---
layout: page
title: TAMS Data Model
subtitle: Content Discovery
hero_image: /images/resources_background.png
show_sidebar: false
---

<style>
  .dm-container {
    display: flex;
    gap: 1.5rem;
    align-items: stretch;
    min-height: 500px;
  }
  @media screen and (max-width: 768px) {
    .dm-container {
      flex-direction: column;
    }
  }
  .dm-diagram {
    flex: 2;
    position: relative;
  }
  .dm-info {
    flex: 1;
    border-left: 4px solid #003e80;
    padding: 1.25rem;
    background: #f8fafd;
    border-radius: 4px;
    overflow-y: auto;
    max-height: 600px;
  }
  .dm-info h3 {
    margin-top: 0;
    color: #003e80;
  }
  .dm-info .placeholder {
    color: #999;
    font-style: italic;
  }

  /* SVG diagram */
  .dm-diagram svg {
    width: 100%;
    height: 100%;
    min-height: 500px;
  }
  .dm-node {
    cursor: pointer;
  }
  .dm-node rect {
    fill: #fff;
    stroke: #003e80;
    stroke-width: 2;
    rx: 6;
    ry: 6;
    transition: all 0.2s ease;
  }
  .dm-node:hover rect {
    fill: #f0f6ff;
    stroke-width: 3;
  }
  .dm-node.is-active rect {
    fill: #e0edff;
    stroke-width: 3;
  }
  .dm-node text {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    font-size: 11px;
    fill: #333;
    text-anchor: middle;
    pointer-events: none;
  }
  .dm-node text.node-type {
    font-size: 9px;
    fill: #666;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }
  .dm-link {
    stroke: #003e80;
    stroke-width: 1.5;
    fill: none;
    opacity: 0.4;
  }
  .dm-link.collection-link {
    stroke-dasharray: 4,3;
    stroke: #e67e22;
    opacity: 0.6;
  }
</style>

<div class="dm-container">
  <div class="dm-diagram">
    <svg viewBox="0 0 700 520" preserveAspectRatio="xMidYMid meet">
      <!-- Links: Source hierarchy (multi-source to mono sources) -->
      <line class="dm-link collection-link" x1="350" y1="70" x2="150" y2="150"/>
      <line class="dm-link collection-link" x1="350" y1="70" x2="300" y2="150"/>
      <line class="dm-link collection-link" x1="350" y1="70" x2="450" y2="150"/>
      <line class="dm-link collection-link" x1="350" y1="70" x2="600" y2="150"/>

      <!-- Links: Multi-source to Multi-flow -->
      <line class="dm-link" x1="350" y1="90" x2="350" y2="230"/>

      <!-- Links: Multi-flow to mono flows (collection) -->
      <line class="dm-link collection-link" x1="350" y1="280" x2="100" y2="360"/>
      <line class="dm-link collection-link" x1="350" y1="280" x2="250" y2="360"/>
      <line class="dm-link collection-link" x1="350" y1="280" x2="400" y2="360"/>
      <line class="dm-link collection-link" x1="350" y1="280" x2="525" y2="360"/>
      <line class="dm-link collection-link" x1="350" y1="280" x2="650" y2="360"/>

      <!-- Links: Mono sources to mono flows -->
      <line class="dm-link" x1="150" y1="180" x2="100" y2="360"/>
      <line class="dm-link" x1="150" y1="180" x2="250" y2="360"/>
      <line class="dm-link" x1="300" y1="180" x2="400" y2="360"/>
      <line class="dm-link" x1="600" y1="180" x2="525" y2="360"/>
      <line class="dm-link" x1="450" y1="180" x2="650" y2="360"/>

      <!-- Row 1: Multi-essence Source -->
      <g class="dm-node" data-node="multi-source">
        <rect x="275" y="30" width="150" height="60"/>
        <text class="node-type" x="350" y="50">Multi Source</text>
        <text x="350" y="70">"Election Night"</text>
      </g>

      <!-- Row 2: Mono Sources -->
      <g class="dm-node" data-node="video-source">
        <rect x="80" y="130" width="140" height="60"/>
        <text class="node-type" x="150" y="150">Video Source</text>
        <text x="150" y="170">Video</text>
      </g>
      <g class="dm-node" data-node="audio-source">
        <rect x="230" y="130" width="140" height="60"/>
        <text class="node-type" x="300" y="150">Audio Source</text>
        <text x="300" y="170">Audio</text>
      </g>
      <g class="dm-node" data-node="data-source">
        <rect x="380" y="130" width="140" height="60"/>
        <text class="node-type" x="450" y="150">Data Source</text>
        <text x="450" y="170">Subtitles</text>
      </g>
      <g class="dm-node" data-node="image-source">
        <rect x="530" y="130" width="140" height="60"/>
        <text class="node-type" x="600" y="150">Image Source</text>
        <text x="600" y="170">Thumbnails</text>
      </g>

      <!-- Row 3: Multi-essence Flow -->
      <g class="dm-node" data-node="multi-flow">
        <rect x="275" y="240" width="150" height="60"/>
        <text class="node-type" x="350" y="260">Multi Flow</text>
        <text x="350" y="280">Programme</text>
      </g>

      <!-- Row 4: Mono Flows -->
      <g class="dm-node" data-node="video-flow-hires">
        <rect x="30" y="350" width="140" height="60"/>
        <text class="node-type" x="100" y="370">Video Flow</text>
        <text x="100" y="390">1080p50 H.264</text>
      </g>
      <g class="dm-node" data-node="video-flow-proxy">
        <rect x="180" y="350" width="140" height="60"/>
        <text class="node-type" x="250" y="370">Video Flow</text>
        <text x="250" y="390">720p Proxy</text>
      </g>
      <g class="dm-node" data-node="audio-flow">
        <rect x="330" y="350" width="140" height="60"/>
        <text class="node-type" x="400" y="370">Audio Flow</text>
        <text x="400" y="390">48kHz PCM</text>
      </g>
      <g class="dm-node" data-node="image-flow">
        <rect x="480" y="350" width="130" height="60"/>
        <text class="node-type" x="545" y="370">Image Flow</text>
        <text x="545" y="390">Thumbnails</text>
      </g>
      <g class="dm-node" data-node="data-flow">
        <rect x="585" y="350" width="110" height="60"/>
        <text class="node-type" x="640" y="370">Data Flow</text>
        <text x="640" y="390">Subtitles</text>
      </g>

      <!-- Legend -->
      <g transform="translate(20, 460)">
        <line x1="0" y1="8" x2="30" y2="8" stroke="#003e80" stroke-width="1.5" opacity="0.4"/>
        <text x="35" y="12" font-size="10" fill="#666" font-family="sans-serif">Belongs to (Source → Flow)</text>
        <line x1="250" y1="8" x2="280" y2="8" stroke="#e67e22" stroke-width="1.5" stroke-dasharray="4,3" opacity="0.6"/>
        <text x="285" y="12" font-size="10" fill="#666" font-family="sans-serif">Collection (Multi collects Mono)</text>
      </g>
    </svg>
  </div>

  <div class="dm-info" id="dm-info-panel">
    <p class="placeholder">Click any element in the diagram to see its details.</p>
  </div>
</div>

<script>
(function() {
  var descriptions = {
    'multi-source': {
      title: 'Multi-Essence Source',
      content: '<p>The <strong>Multi-Essence Source</strong> represents the complete piece of content as a user would understand it — in this case "Election Night Coverage".</p><p>It collects together the individual mono-essence Sources (video, audio, data, images) into a single discoverable entity.</p><p><strong>Key points:</strong></p><ul><li>This is what a user searches for in a MAM or browse tool</li><li>Created automatically when a Multi-Essence Flow is created</li><li>Carries editorial metadata: label, description, tags</li><li>The collection links are managed by the store</li></ul>'
    },
    'video-source': {
      title: 'Video Source',
      content: '<p>The <strong>Video Source</strong> represents all video renditions of this content, regardless of resolution or codec.</p><p><strong>Key points:</strong></p><ul><li>Multiple Flows can belong to this Source (e.g. high-res and proxy)</li><li>Created when the first video Flow referencing it is created</li><li>Collected by the Multi-Essence Source above</li><li>Business logic selects the appropriate Flow for the task at hand</li></ul>'
    },
    'audio-source': {
      title: 'Audio Source',
      content: '<p>The <strong>Audio Source</strong> represents all audio renditions of this content.</p><p><strong>Key points:</strong></p><ul><li>Could have multiple Flows (e.g. PCM and AAC, or different language tracks)</li><li>Collected by the Multi-Essence Source</li><li>Separate from video — enabling independent audio workflows</li></ul>'
    },
    'data-source': {
      title: 'Data Source',
      content: '<p>The <strong>Data Source</strong> represents non-media data associated with this content — in this example, subtitles.</p><p><strong>Key points:</strong></p><ul><li>Data Sources handle any non-audio/video essence: subtitles, closed captions, ancillary data</li><li>Collected by the Multi-Essence Source alongside video and audio</li><li>Flows under this Source hold the format details (e.g. WebVTT, TTML)</li></ul>'
    },
    'image-source': {
      title: 'Image Source',
      content: '<p>The <strong>Image Source</strong> represents still image content — in this example, thumbnail images for preview/navigation.</p><p><strong>Key points:</strong></p><ul><li>Used for poster frames, thumbnails, sprite sheets</li><li>Collected by the Multi-Essence Source</li><li>Flows specify image format and resolution</li><li>Segments use instantaneous timeranges (single timestamp rather than a range)</li></ul>'
    },
    'multi-flow': {
      title: 'Multi-Essence Flow',
      content: '<p>The <strong>Multi-Essence Flow</strong> collects the individual mono-essence Flows together into a single "programme" representation.</p><p><strong>Key points:</strong></p><ul><li>Has no media stored directly against it — no Segments</li><li>Collects mono-essence Flows with defined roles (e.g. "video", "audio")</li><li>Creating this Flow triggers creation of the Multi-Essence Source</li><li>The store auto-resolves Source collections from Flow collections</li><li>Represents the complete rendition a playout system would consume</li></ul>'
    },
    'video-flow-hires': {
      title: 'Video Flow — High Resolution',
      content: '<p>The <strong>1080p50 H.264 Video Flow</strong> is the full-quality video rendition.</p><p><strong>Key points:</strong></p><ul><li>Belongs to the Video Source</li><li>Collected by the Multi-Essence Flow</li><li>Carries technical parameters: codec (H.264), resolution (1920x1080), frame rate (50fps)</li><li>Has its own timeline where video Segments are registered</li><li>Used for transmission, rendering, and final output</li></ul>'
    },
    'video-flow-proxy': {
      title: 'Video Flow — Proxy',
      content: '<p>The <strong>720p Proxy Video Flow</strong> is a lightweight rendition for editing and review.</p><p><strong>Key points:</strong></p><ul><li>Belongs to the same Video Source as the high-res Flow</li><li>Also collected by the Multi-Essence Flow</li><li>Lower resolution and bit rate for fast editorial workflows</li><li>Timeline is aligned with the high-res Flow — same time ranges map to the same content</li><li>Edit decisions made on proxy can be conformed to high-res by switching Flow reference</li></ul>'
    },
    'audio-flow': {
      title: 'Audio Flow',
      content: '<p>The <strong>48kHz PCM Audio Flow</strong> is the audio rendition for this content.</p><p><strong>Key points:</strong></p><ul><li>Belongs to the Audio Source</li><li>Collected by the Multi-Essence Flow</li><li>Parameters: sample rate (48kHz), bit depth (24-bit), codec (PCM)</li><li>Mono-essence — contains audio only</li><li>Could have sibling Flows for compressed formats (AAC) or alternate languages</li></ul>'
    },
    'image-flow': {
      title: 'Image Flow — Thumbnails',
      content: '<p>The <strong>Thumbnail Image Flow</strong> provides preview images at points along the timeline.</p><p><strong>Key points:</strong></p><ul><li>Belongs to the Image Source</li><li>Collected by the Multi-Essence Flow</li><li>Segments use instantaneous timeranges pointing to individual image Objects</li><li>Used by browse tools and timeline scrubbing UIs</li><li>Format parameters specify image codec and resolution</li></ul>'
    },
    'data-flow': {
      title: 'Data Flow — Subtitles',
      content: '<p>The <strong>Subtitle Data Flow</strong> holds the subtitle track for this content.</p><p><strong>Key points:</strong></p><ul><li>Belongs to the Data Source</li><li>Collected by the Multi-Essence Flow</li><li>Segments map time ranges to subtitle file Objects (e.g. WebVTT chunks)</li><li>Multiple Data Flows could exist for different languages</li><li>Format parameters indicate the subtitle format</li></ul>'
    }
  };

  var nodes = document.querySelectorAll('.dm-node');
  var infoPanel = document.getElementById('dm-info-panel');

  nodes.forEach(function(node) {
    node.addEventListener('click', function() {
      nodes.forEach(function(n) { n.classList.remove('is-active'); });
      node.classList.add('is-active');

      var key = node.getAttribute('data-node');
      var info = descriptions[key];
      if (info) {
        infoPanel.innerHTML = '<h3>' + info.title + '</h3>' + info.content;
      }
    });
  });
})();
</script>
