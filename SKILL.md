---
name: design-heist
description: Authorized web clone orchestration skill for turning a user-owned, licensed, or internal-reference webpage URL/screenshots into a high-fidelity local rebuild. Use when the user asks to clone, reproduce, reconstruct, pixel-match, or visually regression-test a website and wants the combined workflow of web-clone-prompt, GSAP motion implementation, verification-before-completion, and systematic-debugging. First produce or confirm a deterministic clone prompt, then build only after user confirmation, implement complex motion with GSAP when appropriate, verify with screenshots/build checks, and debug root causes before claiming completion. Do not use for unauthorized public reuse of third-party brands, assets, copy, paywalled content, or creator-center publishing automation.
---

# Design Heist

## Purpose

Use this as the top-level workflow for authorized website reconstruction. The job is not to "steal" production assets. The job is to capture layout, interaction craft, motion behavior, and visual system decisions, then rebuild them with legal assets and evidence-backed verification.

This skill combines four existing capabilities:

- `$web-clone-prompt` for deterministic clone prompts from URL or screenshots.
- `$gsap-core`, `$gsap-react`, and `$gsap-scrolltrigger` for complex motion, timelines, scroll, parallax, and React cleanup.
- `$verification-before-completion` before any completion claim.
- `$systematic-debugging` whenever the clone diverges, fails, jitters, or breaks.

## Non-Negotiable Boundaries

- Work only on user-owned, licensed, authorized, internal research, or local visual regression targets.
- For third-party commercial pages, replace brand names, logos, copyrighted images/video, proprietary copy, and paid fonts before production use.
- Browser automation may inspect and screenshot public pages for analysis, but do not automate platform publishing flows or creator-center UI publishing.
- Prompt-first is mandatory: do not start coding until the clone prompt exists and the user confirms local implementation.
- Evidence beats vibes: no "looks close" completion without fresh build and visual checks.

## Workflow

### 1. Scope And Evidence

Identify the input mode:

- URL: inspect DOM, computed styles, assets, fonts, scripts, runtime states, opening sequence, hover, scroll, and responsive behavior.
- Screenshot: treat each image as a reference frame; visible pixels are facts, missing sections are labeled inference.
- URL plus screenshots: use URL for exact values and screenshots for visual truth.

If authorization, publication intent, or asset reuse is ambiguous, state the safe assumption: internal reconstruction only, replace protected assets before public release.

### 2. Generate The Clone Prompt

Invoke `$web-clone-prompt` behavior first. Produce a deterministic prompt that pins:

- page map and section order
- exact typography and loadable font sources
- color tokens with hex/rgba and target surfaces
- layout constraints, spacing, breakpoints, and z-index/layer contracts
- asset URLs or generation briefs, never `REPLACE-ME`
- copy boundaries: transcribed only when authorized, otherwise rewritten/replaced
- motion primitives: opening sequence, hover, cursor, scroll, canvas/WebGL, or inferred micro-motion
- verification plan: desktop, mobile, full-page, interaction, and regression checkpoints

Stop after the prompt and ask whether to continue building locally.

### 3. Build After Confirmation

When the user confirms implementation, create or use a local project according to the task context. Prefer:

- React + Vite + TypeScript for app-like clones.
- Tailwind only when exact utility control helps; audit container defaults.
- GSAP when animation quality matters more than simple declarative transitions.
- Plain CSS/WAAPI for simple fades, static hover, or one-off micro-interactions.

Use existing project conventions and AGENTS.md first. Do not introduce a new stack if the repo already has a suitable frontend setup.

### 4. Motion Escalation Rules

Use GSAP skills when the source includes any of these:

- scroll-linked animation, sticky pinning, scrubbed timeline, horizontal scroll, or parallax
- staged opening sequence or hero reveal
- coordinated multi-element timelines
- cursor-following effects, magnetic hover, variable-font motion, or repeated interruptible states
- React components that need animation cleanup on unmount

Load the narrow GSAP skill needed:

- `$gsap-core` for tweens, eases, stagger, timelines, matchMedia, reduced motion.
- `$gsap-react` for React refs, `useGSAP`, `gsap.context`, and cleanup.
- `$gsap-scrolltrigger` for scroll, pinning, scrub, parallax, and scroll-state verification.

Do not use GSAP for trivial effects where CSS is clearer.

### 5. Verification Gate

Before claiming the clone is done, apply `$verification-before-completion`:

- run the project build/typecheck/lint command available in the repo
- start or use a local preview when needed
- capture desktop and mobile screenshots
- compare against the source frames or URL states
- verify key interactions: rest, hover, scroll anchors, opening sequence, and responsive states
- record known differences instead of hiding them

Completion can only be claimed with fresh command output and screenshot/interaction evidence.

### 6. Debugging Gate

If anything is off, apply `$systematic-debugging` before changing code:

- identify the exact mismatch: font, color, layout, layer, asset, timing, scroll state, or responsive breakpoint
- gather source evidence: computed styles, bounding boxes, screenshots, transforms, network assets, or animation state
- form one root-cause hypothesis at a time
- fix the cause, not the symptom
- rerun the smallest useful verification

Common root causes: Tailwind container defaults, missing font weights, protected assets, wrong viewport/DPR, initial animation state captured as final state, unverified mobile breakpoints, and React state driving per-frame animation.

## Final Response Shape

Report only high-signal outcomes:

- clone prompt delivered or local build path
- preview URL if a dev server is running
- verification commands and whether they passed
- screenshot/compare artifacts
- remaining known gaps and why they exist

Never imply unauthorized production readiness. Say clearly when assets, copy, or brand marks must be replaced before public use.
