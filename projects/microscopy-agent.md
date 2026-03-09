---
layout: project
title: AI Agent for Autonomous Image Acquisition and Multimodal Analysis
---

<h1 class="project-page__title">AI Agent for Autonomous Image Acquisition and Multimodal Analysis</h1>
<p class="project-page__subtitle">Research &amp; Application</p>

<div class="project-page__body">

  <img src="/assets/images/Projects/microscopy-agent.png" alt="AI Agent for Autonomous Image Acquisition and Multimodal Analysis" class="project-page__cover">

  <p>
    This project introduces a comprehensive AI orchestration framework designed to automate and enhance Carl Zeiss X-ray Microscopy (XRM) workflows. By combining Large Language Models (LLMs) with Model-Context Protocol (MCP) servers, the system allows scientists to control hardware, acquire images, and run complex analyses using plain-language commands.
  </p>

  <p>
    The platform integrates two core systems into a unified LangGraph multi-agent state machine.
  </p>

  <h2>The Supervisor-Agent Architecture</h2>

  <p>
    The core orchestration relies on a hierarchical structure where a central Supervisor manages the workflow. The Supervisor queries the Skills, generates a step-by-step plan, breaks this plan into tasks, and assigns these tasks downward to the specialized agents.
  </p>

  <ul>
    <li>
      <strong>Instrument Agent:</strong> Operates in a continuous ReAct loop to control physical hardware via the proprietary XradiaPy API, managing axis movement, X-ray states, and image acquisition.
    </li>
    <li>
      <strong>Image Agent:</strong> Handles critical spatial and computational tasks, including 2D/3D segmentation, pixel-to-micron conversions, and stage recentering mathematics.
    </li>
    <li>
      <strong>Multimodal Vision Agent (AutotestAgent):</strong> Runs parallel to the other agents as a third specialized agent to manage an automated quality assurance pipeline for 3D CT reconstructions.
    </li>
  </ul>

  <h2>Multimodal QA and Visual Analysis</h2>

  <p>
    The AutotestAgent drives multiple ZEISS reconstruction executables (FDK, NLM, DRIQ, DRIC) and evaluates them to ensure optimal image clarity. It accomplishes this through a rigorous four-phase pipeline:
  </p>

  <ul>
    <li>
      <strong>Slide Image Extraction:</strong> Exports generated report slides as high-resolution PNG images.
    </li>
    <li>
      <strong>Perceptual Image Quality Assessment (IQA):</strong> Computes blurriness, sharpness, and contrast metrics, replacing standard SSIM with Learned Perceptual Image Patch Similarity (LPIPS) to better correlate with human perception of reconstruction quality.
    </li>
    <li>
      <strong>Multi-Image Comparative Visual Chain-of-Thought:</strong> Batches all algorithm outputs and orthogonal views into a single Claude (claude-sonnet-4-6) call, enabling the AI to detect XRM-specific artifacts and rank the algorithms.
    </li>
    <li>
      <strong>Report Assembly:</strong> Generates a structured JSON file with full numeric metrics and an annotated PowerPoint appendix highlighting the recommended algorithm and specific artifacts.
    </li>
  </ul>

  <h2>System Capabilities</h2>

  <p>
    This ecosystem is supported by a suite of specialized MCP servers for spatial calculations. Ultimately, the integration creates an end-to-end autonomous environment where researchers can seamlessly transition from physical data acquisition to advanced, multi-algorithm reconstruction analysis.
  </p>

</div>
