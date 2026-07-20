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
    min-height: 560px;
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
  .dm-diagram svg {
    width: 100%;
    height: 100%;
    min-height: 560px;
  }
  .dm-node {
    cursor: pointer;
    transition: filter 0.2s ease;
  }
  .dm-node:hover {
    filter: brightness(0.95);
  }
  .dm-node.is-active rect {
    stroke-width: 3.5;
    filter: drop-shadow(0 2px 6px rgba(0,0,0,0.2));
  }
  .dm-node rect {
    stroke-width: 2;
    rx: 8;
    ry: 8;
  }
  .dm-node text {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    fill: #333;
    text-anchor: middle;
    pointer-events: none;
  }
  .dm-node text.node-label {
    font-size: 11px;
    font-weight: 600;
  }
  .dm-node text.node-sublabel {
    font-size: 9.5px;
    fill: #555;
  }
  .dm-node text.node-icon {
    font-family: "Font Awesome 5 Free";
    font-weight: 900;
    font-size: 14px;
    fill: #fff;
  }
  .dm-link {
    fill: none;
    stroke-width: 1.5;
    opacity: 0.5;
  }
  .dm-link.belongs {
    stroke: #555;
  }
  .dm-link.collection {
    stroke: #003e80;
    stroke-dasharray: 5,3;
    opacity: 0.6;
  }
</style>

<div class="dm-container">
  <div class="dm-diagram">
    <svg viewBox="0 0 820 560" preserveAspectRatio="xMidYMid meet">
      <defs>
        <marker id="arrow" markerWidth="8" markerHeight="6" refX="8" refY="3" orient="auto">
          <path d="M0,0 L8,3 L0,6 Z" fill="#555" opacity="0.5"/>
        </marker>
        <marker id="arrow-blue" markerWidth="8" markerHeight="6" refX="8" refY="3" orient="auto">
          <path d="M0,0 L8,3 L0,6 Z" fill="#003e80" opacity="0.6"/>
        </marker>
      </defs>

      <!-- === LINKS === -->

      <!-- Multi-Source to mono Sources (collection - dashed) -->
      <path class="dm-link collection" d="M410,85 C410,125 155,130 155,165" marker-end="url(#arrow-blue)"/>
      <path class="dm-link collection" d="M410,85 C410,125 345,130 345,165" marker-end="url(#arrow-blue)"/>
      <path class="dm-link collection" d="M410,85 C410,125 530,130 530,165" marker-end="url(#arrow-blue)"/>
      <path class="dm-link collection" d="M410,85 C410,125 700,130 700,165" marker-end="url(#arrow-blue)"/>

      <!-- Multi-Source to Multi-Flow (belongs) -->
      <line class="dm-link belongs" x1="410" y1="85" x2="410" y2="260" marker-end="url(#arrow)"/>

      <!-- Multi-Flow to mono Flows (collection - dashed) -->
      <path class="dm-link collection" d="M410,315 C410,355 120,360 120,395" marker-end="url(#arrow-blue)"/>
      <path class="dm-link collection" d="M410,315 C410,355 150,365 150,420" marker-end="url(#arrow-blue)"/>
      <path class="dm-link collection" d="M410,315 C410,355 350,360 350,400" marker-end="url(#arrow-blue)"/>
      <path class="dm-link collection" d="M410,315 C410,355 530,360 530,400" marker-end="url(#arrow-blue)"/>
      <path class="dm-link collection" d="M410,315 C410,355 710,360 710,400" marker-end="url(#arrow-blue)"/>

      <!-- Mono Sources to their Flows (belongs - solid) -->
      <line class="dm-link belongs" x1="155" y1="220" x2="120" y2="395" marker-end="url(#arrow)"/>
      <line class="dm-link belongs" x1="155" y1="220" x2="150" y2="420" marker-end="url(#arrow)"/>
      <line class="dm-link belongs" x1="345" y1="220" x2="350" y2="400" marker-end="url(#arrow)"/>
      <line class="dm-link belongs" x1="530" y1="220" x2="530" y2="400" marker-end="url(#arrow)"/>
      <line class="dm-link belongs" x1="700" y1="220" x2="710" y2="400" marker-end="url(#arrow)"/>

      <!-- === ROW 1: Multi-Essence Source === -->
      <g class="dm-node" data-node="multi-source">
        <rect x="325" y="30" width="170" height="55" fill="#e8f4f8" stroke="#0077b6"/>
        <circle cx="360" cy="57" r="14" fill="#0077b6"/>
        <text class="node-icon" x="360" y="62">&#xf0e8;</text>
        <text class="node-label" x="435" y="54">Election Night</text>
        <text class="node-sublabel" x="435" y="68">Multi-Essence Source</text>
      </g>

      <!-- === ROW 2: Mono Sources === -->
      <g class="dm-node" data-node="video-source">
        <rect x="80" y="165" width="150" height="55" fill="#e8f4f8" stroke="#0077b6"/>
        <circle cx="115" cy="192" r="14" fill="#0077b6"/>
        <text class="node-icon" x="115" y="197">&#xf03d;</text>
        <text class="node-label" x="180" y="189">Video</text>
        <text class="node-sublabel" x="180" y="203">Source</text>
      </g>
      <g class="dm-node" data-node="audio-source">
        <rect x="270" y="165" width="150" height="55" fill="#e8f4f8" stroke="#0077b6"/>
        <circle cx="305" cy="192" r="14" fill="#0077b6"/>
        <text class="node-icon" x="305" y="197">&#xf130;</text>
        <text class="node-label" x="370" y="189">Audio</text>
        <text class="node-sublabel" x="370" y="203">Source</text>
      </g>
      <g class="dm-node" data-node="image-source">
        <rect x="455" y="165" width="150" height="55" fill="#e8f4f8" stroke="#0077b6"/>
        <circle cx="490" cy="192" r="14" fill="#0077b6"/>
        <text class="node-icon" x="490" y="197">&#xf03e;</text>
        <text class="node-label" x="555" y="189">Thumbnails</text>
        <text class="node-sublabel" x="555" y="203">Image Source</text>
      </g>
      <g class="dm-node" data-node="data-source">
        <rect x="625" y="165" width="150" height="55" fill="#e8f4f8" stroke="#0077b6"/>
        <circle cx="660" cy="192" r="14" fill="#0077b6"/>
        <text class="node-icon" x="660" y="197">&#xf1ea;</text>
        <text class="node-label" x="725" y="189">Subtitles</text>
        <text class="node-sublabel" x="725" y="203">Data Source</text>
      </g>

      <!-- === ROW 3: Multi-Essence Flow === -->
      <g class="dm-node" data-node="multi-flow">
        <rect x="325" y="260" width="170" height="55" fill="#fef3e8" stroke="#e67e22"/>
        <circle cx="360" cy="287" r="14" fill="#e67e22"/>
        <text class="node-icon" x="360" y="292">&#xf0e8;</text>
        <text class="node-label" x="435" y="284">Programme</text>
        <text class="node-sublabel" x="435" y="298">Multi-Essence Flow</text>
      </g>

      <!-- === ROW 4: Mono Flows === -->
      <!-- Video Flows - stacked/overlapping to show they're a set -->
      <g class="dm-node" data-node="video-flow-proxy">
        <rect x="75" y="420" width="150" height="55" fill="#fef3e8" stroke="#e67e22"/>
        <circle cx="110" cy="447" r="14" fill="#e67e22"/>
        <text class="node-icon" x="110" y="452">&#xf03d;</text>
        <text class="node-label" x="175" y="440">720p Proxy</text>
        <text class="node-sublabel" x="175" y="454">Video Flow</text>
      </g>
      <g class="dm-node" data-node="video-flow-hires">
        <rect x="45" y="395" width="150" height="55" fill="#fef3e8" stroke="#e67e22"/>
        <circle cx="80" cy="422" r="14" fill="#e67e22"/>
        <text class="node-icon" x="80" y="427">&#xf03d;</text>
        <text class="node-label" x="145" y="415">1080p50 H.264</text>
        <text class="node-sublabel" x="145" y="429">Video Flow</text>
      </g>
      <g class="dm-node" data-node="audio-flow">
        <rect x="280" y="400" width="140" height="55" fill="#fef3e8" stroke="#e67e22"/>
        <circle cx="315" cy="427" r="14" fill="#e67e22"/>
        <text class="node-icon" x="315" y="432">&#xf130;</text>
        <text class="node-label" x="375" y="420">48kHz PCM</text>
        <text class="node-sublabel" x="375" y="434">Audio Flow</text>
      </g>
      <g class="dm-node" data-node="image-flow">
        <rect x="460" y="400" width="140" height="55" fill="#fef3e8" stroke="#e67e22"/>
        <circle cx="495" cy="427" r="14" fill="#e67e22"/>
        <text class="node-icon" x="495" y="432">&#xf03e;</text>
        <text class="node-label" x="555" y="420">Thumbnails</text>
        <text class="node-sublabel" x="555" y="434">Image Flow</text>
      </g>
      <g class="dm-node" data-node="data-flow">
        <rect x="640" y="400" width="140" height="55" fill="#fef3e8" stroke="#e67e22"/>
        <circle cx="675" cy="427" r="14" fill="#e67e22"/>
        <text class="node-icon" x="675" y="432">&#xf1ea;</text>
        <text class="node-label" x="735" y="420">Subtitles</text>
        <text class="node-sublabel" x="735" y="434">Data Flow</text>
      </g>

      <!-- === LEGEND === -->
      <g transform="translate(30, 490)">
        <text font-size="10" font-weight="600" fill="#333" font-family="sans-serif">Legend:</text>

        <line x1="60" y1="0" x2="95" y2="0" stroke="#555" stroke-width="1.5" opacity="0.5"/>
        <polygon points="95,-3 101,0 95,3" fill="#555" opacity="0.5"/>
        <text x="108" y="4" font-size="10" fill="#666" font-family="sans-serif">Belongs to</text>

        <line x1="200" y1="0" x2="235" y2="0" stroke="#003e80" stroke-width="1.5" stroke-dasharray="5,3" opacity="0.6"/>
        <polygon points="235,-3 241,0 235,3" fill="#003e80" opacity="0.6"/>
        <text x="248" y="4" font-size="10" fill="#666" font-family="sans-serif">Collection</text>

        <rect x="350" y="-7" width="14" height="14" rx="3" fill="#e8f4f8" stroke="#0077b6" stroke-width="1.5"/>
        <text x="370" y="4" font-size="10" fill="#666" font-family="sans-serif">Source</text>

        <rect x="430" y="-7" width="14" height="14" rx="3" fill="#fef3e8" stroke="#e67e22" stroke-width="1.5"/>
        <text x="450" y="4" font-size="10" fill="#666" font-family="sans-serif">Flow</text>
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
      title: 'Data Source — Subtitles',
      content: '<p>The <strong>Data Source</strong> represents non-media data associated with this content — in this example, subtitles.</p><p><strong>Key points:</strong></p><ul><li>Data Sources handle any non-audio/video essence: subtitles, closed captions, ancillary data</li><li>Collected by the Multi-Essence Source alongside video and audio</li><li>Flows under this Source hold the format details (e.g. WebVTT, TTML)</li></ul>'
    },
    'image-source': {
      title: 'Image Source — Thumbnails',
      content: '<p>The <strong>Image Source</strong> represents still image content — in this example, thumbnail images for preview and navigation.</p><p><strong>Key points:</strong></p><ul><li>Used for poster frames, thumbnails, sprite sheets</li><li>Collected by the Multi-Essence Source</li><li>Flows specify image format and resolution</li><li>Segments use instantaneous timeranges (single timestamp rather than a range)</li></ul>'
    },
    'multi-flow': {
      title: 'Multi-Essence Flow',
      content: '<p>The <strong>Multi-Essence Flow</strong> collects the individual mono-essence Flows together into a single "programme" representation.</p><p><strong>Key points:</strong></p><ul><li>Has no media stored directly against it — no Segments</li><li>Collects mono-essence Flows with defined roles (e.g. "video", "audio")</li><li>Creating this Flow triggers creation of the Multi-Essence Source</li><li>The store auto-resolves Source collections from Flow collections</li><li>Represents the complete rendition a playout system would consume</li></ul>'
    },
    'video-flow-hires': {
      title: 'Video Flow — High Resolution',
      content: '<p>The <strong>1080p50 H.264 Video Flow</strong> is the full-quality video rendition.</p><p><strong>Key points:</strong></p><ul><li>Belongs to the Video Source</li><li>Collected by the Multi-Essence Flow</li><li>Carries technical parameters: codec (H.264), resolution (1920×1080), frame rate (50fps)</li><li>Has its own timeline where video Segments are registered</li><li>Used for transmission, rendering, and final output</li></ul>'
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

  function selectNode(node) {
    nodes.forEach(function(n) { n.classList.remove('is-active'); });
    node.classList.add('is-active');

    var key = node.getAttribute('data-node');
    var info = descriptions[key];
    if (info) {
      infoPanel.innerHTML = '<h3>' + info.title + '</h3>' + info.content;
    }
  }

  nodes.forEach(function(node) {
    node.addEventListener('click', function() {
      selectNode(node);
    });
  });

  // Select multi-source by default on load
  var defaultNode = document.querySelector('.dm-node[data-node="multi-source"]');
  if (defaultNode) {
    selectNode(defaultNode);
  }
})();
</script>
