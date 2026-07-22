---
layout: page
title: Time Addressable Media Store
subtitle: Home of the TAMS community and latest news
show_sidebar: true
hero_image: /images/home_background.png
hero_height: is-small
---

## What is TAMS?

The Time Addressable Media Store (TAMS) is an open-source API specification based on a practical implementation of [Time Addressable Media principles](https://www.bbc.co.uk/rd/publications/tam) developed by BBC Research & Development. TAMS is designed around storing media chunks in object storage, presented through an open API that enables content-centric workflows rather than traditional file-based approaches.

<div class="video-wrapper" style="text-align: center;">
<div style="position: relative; padding-bottom: 56.25%; max-width: 720px; margin: 0 auto; height: 0; overflow: hidden;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/W7WAV65duj0?si=OjyA3Diy2Y-8m-nr" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>
</div>

## Key Benefits

<style>
  .benefits-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1.25rem;
    margin-top: 1.5rem;
  }
  @media screen and (max-width: 768px) {
    .benefits-grid {
      grid-template-columns: 1fr;
    }
  }
  .benefits-grid .last-tile {
    grid-column: 1 / -1;
    max-width: 50%;
    justify-self: center;
  }
  @media screen and (max-width: 768px) {
    .benefits-grid .last-tile {
      max-width: 100%;
    }
  }
  .benefit-tile {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 0.75rem;
    padding: 1.5rem;
    border: 2px solid #e8e8e8;
    border-radius: 8px;
    transition: all 0.2s ease;
    width: 100%;
  }
  .benefit-tile:hover {
    border-color: #003e80;
    box-shadow: 0 2px 10px rgba(0, 62, 128, 0.1);
  }
  .benefit-tile .benefit-icon {
    color: #003e80;
  }
  .benefit-tile .benefit-body h4 {
    margin: 0 0 0.5rem 0;
    font-size: 1.2rem;
    font-weight: 700;
    color: #333;
  }
  .benefit-tile .benefit-body p {
    margin: 0;
    font-size: 0.9rem;
    color: #555;
    line-height: 1.5;
  }
</style>

<div class="benefits-grid">
  <div class="benefit-tile">
    <div class="benefit-icon">
      <span class="icon is-large"><i class="fas fa-compress-arrows-alt fa-3x"></i></span>
    </div>
    <div class="benefit-body">
      <h4>Convergence</h4>
      <p>A single TAMS store can serve multiple different purposes and business units. This includes the broadcast, post-production, social media, and VOD teams all being able to source content from a single store.</p>
    </div>
  </div>
  <div class="benefit-tile">
    <div class="benefit-icon">
      <span class="icon is-large"><i class="fas fa-hand-holding-usd fa-3x"></i></span>
    </div>
    <div class="benefit-body">
      <h4>Cost Effective</h4>
      <p>By using cloud-based technologies and focusing on the use of commodity object storage, removes the need for high performance file systems and de-duplicate the storage. Adding serverless technologies means using TAMS should be significantly cheaper than the traditional approach.</p>
    </div>
  </div>
  <div class="benefit-tile">
    <div class="benefit-icon">
      <span class="icon is-large"><i class="fas fa-puzzle-piece fa-3x"></i></span>
    </div>
    <div class="benefit-body">
      <h4>Interoperability</h4>
      <p>With vendors adopting a common API specification, this should provide interoperability between products supporting the TAMS API, allowing customers to pick and chose the tools they want to use.</p>
    </div>
  </div>
  <div class="benefit-tile">
    <div class="benefit-icon">
      <span class="icon is-large"><i class="fas fa-lock-open fa-3x"></i></span>
    </div>
    <div class="benefit-body">
      <h4>Open Framework</h4>
      <p>The TAMS API is an open source specification. This means that any customer or partner can start building around it without needing the support of a single vendor for proprietary technology or license fees.</p>
    </div>
  </div>
  <div class="benefit-tile">
    <div class="benefit-icon">
      <span class="icon is-large"><i class="fas fa-cubes fa-3x"></i></span>
    </div>
    <div class="benefit-body">
      <h4>Bringing Together Live and File</h4>
      <p>TAMS is based on the same core reference architecture as Networked Media Open Specifications (NMOS). This means it's possible to preserve both the timing and identity for content between the live and stored domains, simplifying workflows.</p>
    </div>
  </div>
  <div class="benefit-tile">
    <div class="benefit-icon">
      <span class="icon is-large"><i class="fas fa-cloud fa-3x"></i></span>
    </div>
    <div class="benefit-body">
      <h4>Elasticity</h4>
      <p>The use of the cloud and cloud-based technologies means that a TAMS solution should be able to scale both up and down with the business need. This is particularly key in live environments where the workloads are rarely constant.</p>
    </div>
  </div>
  <div class="benefit-tile last-tile">
    <div class="benefit-icon">
      <span class="icon is-large"><i class="fas fa-rocket fa-3x"></i></span>
    </div>
    <div class="benefit-body">
      <h4>Workflow Acceleration</h4>
      <p>The ability to access segments as soon as they are written to the store and the use of "edit by reference" workflows means that workflows can be achieved faster than traditional file-based approaches.</p>
    </div>
  </div>
</div>
