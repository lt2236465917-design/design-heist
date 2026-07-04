# Design Heist

`design-heist` is a Codex skill for rebuilding authorized websites with higher visual fidelity.

It does not simply say "make something similar." It turns a URL or screenshots into a clear clone prompt, waits for your confirmation, then guides Codex through implementation, motion work, verification, and debugging.

## What It Does

Design Heist combines four jobs into one workflow:

1. **Clone prompt**  
   It first uses a prompt-first workflow to describe the target page precisely: layout, typography, colors, assets, copy boundaries, motion, responsive behavior, and verification steps.

2. **Local implementation**  
   After you confirm, Codex can use that prompt to build the page locally.

3. **Motion reconstruction**  
   For complex animation, it routes Codex toward GSAP patterns: timelines, scroll-triggered motion, parallax, staged hero reveals, hover states, and React cleanup.

4. **Verification and repair**  
   Before calling the work finished, Codex must run build checks, capture screenshots, compare key states, and debug mismatches from root cause.

## When To Use It

Use this skill when you want to:

- rebuild your own website from a URL
- turn webpage screenshots into a local prototype
- recreate an authorized landing page for internal study
- do visual regression work against a reference page
- preserve the look, layout, and motion of a page while replacing protected assets
- give Codex a stricter workflow for high-fidelity frontend reconstruction

## When Not To Use It

Do not use this skill to:

- copy third-party websites for public release without permission
- reuse protected logos, brand names, images, videos, fonts, or copy
- bypass paywalls, login-only pages, or private assets
- automate publishing through creator-center UI flows
- clone backend logic, databases, accounts, payments, or private APIs

If the source page is not yours, treat it as internal reference only and replace protected material before production use.

## Why It Helps

Normal AI website cloning often fails because it skips the boring but important parts:

- exact font and color choices
- asset sourcing rules
- scroll and hover states
- opening animations
- mobile breakpoints
- build verification
- screenshot comparison
- root-cause debugging

Design Heist makes those steps explicit. The advantage is not magic. The advantage is a stricter workflow with fewer places for vague guesses to hide.

## Install

Clone this repository into your Codex skills folder:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/lt2236465917-design/design-heist.git ~/.codex/skills/design-heist
```

Restart Codex after installing.

## Usage

Start with:

```text
$design-heist
```

Examples:

```text
$design-heist Rebuild this authorized landing page from its URL: https://example.com
```

```text
$design-heist Turn these screenshots into a clone prompt, then wait for my confirmation before building.
```

```text
$design-heist Recreate our old homepage locally and verify desktop and mobile screenshots.
```

## How The Workflow Runs

1. You provide a URL, screenshots, or both.
2. Codex creates a deterministic clone prompt first.
3. Codex asks whether to continue with local implementation.
4. If you confirm, Codex builds the page using the current project conventions.
5. Complex motion is handled with GSAP when needed.
6. Codex runs build checks and screenshot verification.
7. If the result is off, Codex debugs the cause instead of randomly tweaking styles.

## Dependencies

This skill is an orchestrator. It works best when these skills are also installed:

- `web-clone-prompt`
- `gsap-core`
- `gsap-react`
- `gsap-scrolltrigger`
- `verification-before-completion`
- `systematic-debugging`

If some of them are missing, Codex can still follow the workflow, but the result may be less rigorous.

## License

MIT. Free to use, copy, modify, and share.

