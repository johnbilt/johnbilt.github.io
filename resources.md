---
layout: page
title: Resources
subtitle: All the tools to help get started with TAMS
hero_image: /images/resources_background.png
hero_height: is-small
show_sidebar: false
---

<style>
  .resources-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.25rem;
    margin-top: 1.5rem;
  }
  @media screen and (max-width: 768px) {
    .resources-grid {
      grid-template-columns: 1fr;
    }
  }
  .resource-tile {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 0.75rem;
    padding: 1.5rem;
    border: 2px solid #e8e8e8;
    border-radius: 8px;
    transition: all 0.2s ease;
  }
  .resource-tile:hover {
    border-color: #003e80;
    box-shadow: 0 2px 10px rgba(0, 62, 128, 0.1);
  }
  .resource-tile .resource-icon {
    color: #003e80;
  }
  .resource-tile h4 {
    margin: 0 0 0.4rem 0;
    font-size: 1.1rem;
    font-weight: 700;
    color: #333;
  }
  .resource-tile p {
    margin: 0;
    font-size: 0.9rem;
    color: #555;
    line-height: 1.5;
    flex: 1;
  }
  .resource-tile a.resource-link {
    margin-top: 0.75rem;
    font-size: 0.85rem;
    font-weight: 600;
    color: #003e80;
  }
  .resource-tile a.resource-link:hover {
    text-decoration: underline;
  }
</style>

<div class="resources-grid">
  <div class="resource-tile">
    <div class="resource-icon">
      <span class="icon is-large"><i class="fab fa-github fa-3x"></i></span>
    </div>
    <h4>TAMS API Specification</h4>
    <p>Full specification for the TAMS API from BBC R&D. Includes key app notes on how to implement TAMS, plus records of all changes.</p>
    <a class="resource-link" href="https://github.com/bbc/tams" target="_blank" rel="noopener noreferrer">View on GitHub &rarr;</a>
  </div>
  <div class="resource-tile">
    <div class="resource-icon">
      <span class="icon is-large"><i class="fab fa-aws fa-3x"></i></span>
    </div>
    <h4>Reference TAMS API Implementation</h4>
    <p>Implementation of the TAMS API released by AWS. Designed to assist customers and partners start their journey with TAMS.</p>
    <a class="resource-link" href="https://github.com/awslabs/time-addressable-media-store" target="_blank" rel="noopener noreferrer">View on GitHub &rarr;</a>
  </div>
  <div class="resource-tile">
    <div class="resource-icon">
      <span class="icon is-large"><i class="fas fa-toolbox fa-3x"></i></span>
    </div>
    <h4>TAMS Tools Repository</h4>
    <p>A collection of tools from AWS to complement the API implementation. Includes UI with embedded Omakase player, media processing and more.</p>
    <a class="resource-link" href="https://github.com/awslabs/time-addressable-media-store-tools" target="_blank" rel="noopener noreferrer">View on GitHub &rarr;</a>
  </div>
  <div class="resource-tile">
    <div class="resource-icon">
      <span class="icon is-large"><i class="fab fa-python fa-3x"></i></span>
    </div>
    <h4>TAMS Sample Scripts</h4>
    <p>A set of Python sample scripts to help get started with the TAMS API. Covers common workflows and provides working examples to build on.</p>
    <a class="resource-link" href="https://github.com/aws-solutions-library-samples/guidance-for-cloud-native-fast-turnaround-media-workflows-on-aws" target="_blank" rel="noopener noreferrer">View on GitHub &rarr;</a>
  </div>
  <div class="resource-tile">
    <div class="resource-icon">
      <span class="icon is-large"><i class="fas fa-book-open fa-3x"></i></span>
    </div>
    <h4>AWS TAMS Implementation Guide</h4>
    <p>Comprehensive guide for deploying and configuring the AWS TAMS implementation, including architecture and operational guidance.</p>
    <a class="resource-link" href="https://aws-solutions-library-samples.github.io/media-entertainment/cloud-native-fast-turnaround-media-workflows-on-aws/index.html" target="_blank" rel="noopener noreferrer">View Guide &rarr;</a>
  </div>
  <div class="resource-tile">
    <div class="resource-icon">
      <span class="icon is-large"><i class="fas fa-compass fa-3x"></i></span>
    </div>
    <h4>AWS Guidance for Cloud-Native Fast-Turnaround Media Workflows</h4>
    <p>AWS Solutions Library guidance on building cloud-native fast-turnaround media workflows using TAMS on AWS.</p>
    <a class="resource-link" href="https://aws.amazon.com/solutions/guidance/cloud-native-fast-turnaround-media-workflows-on-aws/" target="_blank" rel="noopener noreferrer">View Guidance &rarr;</a>
  </div>
</div>
