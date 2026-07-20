---
layout: page
title: TAMS Data Model
subtitle: Content Creation
hero_image: /images/resources_background.png
show_sidebar: false
---

<style>
  .dc-container {
    display: flex;
    gap: 1.5rem;
    align-items: stretch;
    min-height: 580px;
  }
  @media screen and (max-width: 768px) {
    .dc-container {
      flex-direction: column-reverse;
    }
  }
  .dc-diagram {
    flex: 2;
    position: relative;
  }
  .dc-info {
    flex: 1;
    border-right: 4px solid #003e80;
    padding: 1.25rem;
    background: #f8fafd;
    border-radius: 4px;
    overflow-y: auto;
    max-height: 620px;
    display: flex;
    flex-direction: column;
  }
  .dc-info h3 {
    margin-top: 0;
    color: #003e80;
  }
  .dc-info .step-description {
    flex: 1;
  }
  .dc-controls {
    display: flex;
    gap: 0.5rem;
    margin-top: 1rem;
    padding-top: 0.75rem;
    border-top: 1px solid #e0e0e0;
    align-items: center;
  }
  .dc-controls button {
    padding: 0.4rem 1rem;
    border: 2px solid #003e80;
    background: #fff;
    color: #003e80;
    border-radius: 4px;
    cursor: pointer;
    font-weight: 600;
    font-size: 0.85rem;
    transition: all 0.2s;
  }
  .dc-controls button:hover:not(:disabled) {
    background: #003e80;
    color: #fff;
  }
  .dc-controls button:disabled {
    opacity: 0.4;
    cursor: not-allowed;
  }
  .dc-controls .step-indicator {
    margin-left: auto;
    font-size: 0.8rem;
    color: #666;
  }

  .dc-diagram svg {
    width: 100%;
    height: 100%;
    min-height: 580px;
  }
  .dc-node {
    opacity: 0;
    transition: opacity 0.5s ease;
  }
  .dc-node.visible {
    opacity: 1;
  }
  .dc-node rect {
    stroke-width: 2;
    rx: 8;
    ry: 8;
  }
  .dc-node.highlight rect {
    stroke-width: 3.5;
    filter: drop-shadow(0 2px 8px rgba(0,0,0,0.25));
  }
  .dc-node text {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    fill: #333;
    text-anchor: middle;
    pointer-events: none;
  }
  .dc-node text.node-label {
    font-size: 11px;
    font-weight: 600;
  }
  .dc-node text.node-sublabel {
    font-size: 9.5px;
    fill: #555;
  }
  .dc-node text.node-icon {
    font-family: "Font Awesome 5 Free";
    font-weight: 900;
    font-size: 14px;
    fill: #fff;
  }
  .dc-link {
    fill: none;
    stroke-width: 1.5;
    opacity: 0;
    transition: opacity 0.5s ease;
  }
  .dc-link.visible {
    opacity: 0.5;
  }
  .dc-link.belongs {
    stroke: #555;
  }
  .dc-link.collection {
    stroke: #003e80;
    stroke-dasharray: 5,3;
  }
  .dc-link.visible.collection {
    opacity: 0.6;
  }
  .dc-action-label {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    font-size: 9px;
    fill: #27ae60;
    font-weight: 600;
    text-anchor: middle;
    opacity: 0;
    transition: opacity 0.5s ease;
  }
  .dc-action-label.visible {
    opacity: 1;
  }
</style>

<div class="dc-container">
  <div class="dc-info" id="dc-info-panel">
    <div class="step-description" id="dc-step-text">
      <h3>Content Creation in TAMS</h3>
      <p>This animated diagram shows the step-by-step process of creating content in a TAMS store.</p>
      <p>Use the <strong>Next</strong> button to walk through each step and see how Sources, Flows, and their relationships are built up.</p>
    </div>
    <div class="dc-controls">
      <button id="dc-prev" disabled>Previous</button>
      <button id="dc-next">Next</button>
      <button id="dc-reset">Reset</button>
      <span class="step-indicator" id="dc-step-indicator">Step 0 / 4</span>
    </div>
  </div>

  <div class="dc-diagram">
    <svg viewBox="0 0 580 520" preserveAspectRatio="xMidYMid meet">
      <defs>
        <marker id="c-arrow" markerWidth="8" markerHeight="6" refX="8" refY="3" orient="auto">
          <path d="M0,0 L8,3 L0,6 Z" fill="#555" opacity="0.5"/>
        </marker>
        <marker id="c-arrow-blue" markerWidth="8" markerHeight="6" refX="8" refY="3" orient="auto">
          <path d="M0,0 L8,3 L0,6 Z" fill="#003e80" opacity="0.6"/>
        </marker>
      </defs>

      <!-- === LINKS === -->

      <!-- Video Flow → Video Source (belongs) -->
      <line class="dc-link belongs" data-step="1" x1="150" y1="355" x2="150" y2="200" marker-end="url(#c-arrow)"/>

      <!-- Audio Flow → Audio Source (belongs) -->
      <line class="dc-link belongs" data-step="2" x1="420" y1="355" x2="420" y2="200" marker-end="url(#c-arrow)"/>

      <!-- Multi Flow → Multi Source (belongs) -->
      <line class="dc-link belongs" data-step="3" x1="290" y1="355" x2="290" y2="80" marker-end="url(#c-arrow)"/>

      <!-- Multi Source → Video Source (collection) -->
      <path class="dc-link collection" data-step="4" d="M290,80 C290,120 150,130 150,155" marker-end="url(#c-arrow-blue)"/>
      <!-- Multi Source → Audio Source (collection) -->
      <path class="dc-link collection" data-step="4" d="M290,80 C290,120 420,130 420,155" marker-end="url(#c-arrow-blue)"/>

      <!-- Multi Flow → Video Flow (collection) -->
      <path class="dc-link collection" data-step="4" d="M290,410 C290,430 150,435 150,410" marker-end="url(#c-arrow-blue)"/>
      <!-- Multi Flow → Audio Flow (collection) -->
      <path class="dc-link collection" data-step="4" d="M290,410 C290,430 420,435 420,410" marker-end="url(#c-arrow-blue)"/>

      <!-- === SOURCES (Row 1 & 2) === -->

      <!-- Multi-Essence Source -->
      <g class="dc-node" data-step="3" data-node="multi-source">
        <rect x="205" y="30" width="170" height="55" fill="#e8f4f8" stroke="#0077b6"/>
        <circle cx="240" cy="57" r="14" fill="#0077b6"/>
        <text class="node-icon" x="240" y="62">&#xf0e8;</text>
        <text class="node-label" x="315" y="54">Programme</text>
        <text class="node-sublabel" x="315" y="68">Multi-Essence Source</text>
      </g>

      <!-- Video Source -->
      <g class="dc-node" data-step="1" data-node="video-source">
        <rect x="75" y="150" width="150" height="55" fill="#e8f4f8" stroke="#0077b6"/>
        <circle cx="110" cy="177" r="14" fill="#0077b6"/>
        <text class="node-icon" x="110" y="182">&#xf03d;</text>
        <text class="node-label" x="175" y="174">Video</text>
        <text class="node-sublabel" x="175" y="188">Source</text>
      </g>

      <!-- Audio Source -->
      <g class="dc-node" data-step="2" data-node="audio-source">
        <rect x="345" y="150" width="150" height="55" fill="#e8f4f8" stroke="#0077b6"/>
        <circle cx="380" cy="177" r="14" fill="#0077b6"/>
        <text class="node-icon" x="380" y="182">&#xf130;</text>
        <text class="node-label" x="445" y="174">Audio</text>
        <text class="node-sublabel" x="445" y="188">Source</text>
      </g>

      <!-- === FLOWS (Row 3) === -->

      <!-- Video Flow -->
      <g class="dc-node" data-step="1" data-node="video-flow">
        <rect x="75" y="355" width="150" height="55" fill="#fef3e8" stroke="#e67e22"/>
        <circle cx="110" cy="382" r="14" fill="#e67e22"/>
        <text class="node-icon" x="110" y="387">&#xf03d;</text>
        <text class="node-label" x="175" y="379">1080p50 H.264</text>
        <text class="node-sublabel" x="175" y="393">Video Flow</text>
      </g>

      <!-- Multi-Essence Flow -->
      <g class="dc-node" data-step="3" data-node="multi-flow">
        <rect x="205" y="355" width="170" height="55" fill="#fef3e8" stroke="#e67e22"/>
        <circle cx="240" cy="382" r="14" fill="#e67e22"/>
        <text class="node-icon" x="240" y="387">&#xf0e8;</text>
        <text class="node-label" x="315" y="379">Programme</text>
        <text class="node-sublabel" x="315" y="393">Multi-Essence Flow</text>
      </g>

      <!-- Audio Flow -->
      <g class="dc-node" data-step="2" data-node="audio-flow">
        <rect x="345" y="355" width="150" height="55" fill="#fef3e8" stroke="#e67e22"/>
        <circle cx="380" cy="382" r="14" fill="#e67e22"/>
        <text class="node-icon" x="380" y="387">&#xf130;</text>
        <text class="node-label" x="445" y="379">48kHz PCM</text>
        <text class="node-sublabel" x="445" y="393">Audio Flow</text>
      </g>

      <!-- === ACTION LABELS === -->
      <text class="dc-action-label" data-step="1" x="150" y="340">CREATE</text>
      <text class="dc-action-label" data-step="1" x="150" y="270" fill="#0077b6">AUTO-CREATED</text>
      <text class="dc-action-label" data-step="2" x="420" y="340">CREATE</text>
      <text class="dc-action-label" data-step="2" x="420" y="270" fill="#0077b6">AUTO-CREATED</text>
      <text class="dc-action-label" data-step="3" x="290" y="340">CREATE</text>
      <text class="dc-action-label" data-step="3" x="290" y="120" fill="#0077b6">AUTO-CREATED</text>
      <text class="dc-action-label" data-step="4" x="290" y="445">COLLECT</text>

      <!-- === LEGEND === -->
      <g transform="translate(20, 470)">
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
</div>

<script>
(function() {
  var currentStep = 0;
  var totalSteps = 4;

  var stepDescriptions = [
    {
      title: 'Content Creation in TAMS',
      content: '<p>This animated diagram shows the step-by-step process of creating content in a TAMS store.</p><p>Use the <strong>Next</strong> button to walk through each step and see how Sources, Flows, and their relationships are built up.</p>'
    },
    {
      title: 'Step 1: Create Video Flow',
      content: '<p>The first action is to <strong>create a Video Flow</strong> specifying the technical parameters (codec, resolution, frame rate) and a Source ID.</p><p>The store automatically creates the <strong>Video Source</strong> because no Source with that ID exists yet. The Source inherits the Flow\'s label and description.</p><p><strong>What you do:</strong> POST to create a video Flow with a source_id</p><p><strong>What the store does:</strong> Creates the Source automatically</p>'
    },
    {
      title: 'Step 2: Create Audio Flow',
      content: '<p>Next, <strong>create an Audio Flow</strong> with its own technical parameters (sample rate, bit depth, codec) and a different Source ID.</p><p>Again, the store automatically creates the <strong>Audio Source</strong> because the referenced Source doesn\'t exist yet.</p><p><strong>What you do:</strong> POST to create an audio Flow with a new source_id</p><p><strong>What the store does:</strong> Creates the Audio Source automatically</p>'
    },
    {
      title: 'Step 3: Create Multi-Essence Flow',
      content: '<p>Now <strong>create a Multi-Essence Flow</strong> with a new Source ID. This Flow has no media stored directly against it — it exists to collect the mono-essence Flows together.</p><p>The store automatically creates the <strong>Multi-Essence Source</strong> — the top-level entity that represents the complete programme.</p><p><strong>What you do:</strong> POST to create a multi-essence Flow with a new source_id</p><p><strong>What the store does:</strong> Creates the Multi-Essence Source automatically</p>'
    },
    {
      title: 'Step 4: Create Flow Collection',
      content: '<p>Finally, <strong>add the Video and Audio Flows to the Multi-Essence Flow\'s collection</strong>. This tells the store which mono-essence Flows make up the programme.</p><p>The store automatically resolves the Source relationships — it links the Video Source and Audio Source into the Multi-Essence Source\'s collection.</p><p><strong>What you do:</strong> PUT to add video and audio Flows to the multi-essence Flow collection</p><p><strong>What the store does:</strong> Creates the collection links between Sources automatically</p>'
    }
  ];

  var prevBtn = document.getElementById('dc-prev');
  var nextBtn = document.getElementById('dc-next');
  var resetBtn = document.getElementById('dc-reset');
  var stepText = document.getElementById('dc-step-text');
  var stepIndicator = document.getElementById('dc-step-indicator');

  function updateDiagram() {
    // Show/hide elements based on current step
    var nodes = document.querySelectorAll('.dc-node');
    var links = document.querySelectorAll('.dc-link');
    var labels = document.querySelectorAll('.dc-action-label');

    nodes.forEach(function(node) {
      var step = parseInt(node.getAttribute('data-step'));
      if (step <= currentStep) {
        node.classList.add('visible');
        // Highlight only the current step's nodes
        if (step === currentStep) {
          node.classList.add('highlight');
        } else {
          node.classList.remove('highlight');
        }
      } else {
        node.classList.remove('visible');
        node.classList.remove('highlight');
      }
    });

    links.forEach(function(link) {
      var step = parseInt(link.getAttribute('data-step'));
      if (step <= currentStep) {
        link.classList.add('visible');
      } else {
        link.classList.remove('visible');
      }
    });

    labels.forEach(function(label) {
      var step = parseInt(label.getAttribute('data-step'));
      if (step === currentStep) {
        label.classList.add('visible');
      } else {
        label.classList.remove('visible');
      }
    });

    // Update description
    var desc = stepDescriptions[currentStep];
    stepText.innerHTML = '<h3>' + desc.title + '</h3>' + desc.content;

    // Update buttons
    prevBtn.disabled = (currentStep === 0);
    nextBtn.disabled = (currentStep === totalSteps);
    stepIndicator.textContent = 'Step ' + currentStep + ' / ' + totalSteps;
  }

  nextBtn.addEventListener('click', function() {
    if (currentStep < totalSteps) {
      currentStep++;
      updateDiagram();
    }
  });

  prevBtn.addEventListener('click', function() {
    if (currentStep > 0) {
      currentStep--;
      updateDiagram();
    }
  });

  resetBtn.addEventListener('click', function() {
    currentStep = 0;
    updateDiagram();
  });

  // Initial state
  updateDiagram();
})();
</script>
