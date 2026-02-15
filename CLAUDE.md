# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Sophizo** ("The Colour of Wisdom") is a static single-page website for a premium hair serum brand. The entire site lives in `index.html` — all HTML, CSS (~687 lines), and JavaScript (~98 lines) are inline in that single file.

There is no build system, package manager, test framework, or linting toolchain. To preview the site, open `index.html` directly in a browser or serve it with any static file server (e.g., `python3 -m http.server`).

## Architecture

### Single-File Structure
All code is in `index.html`. The file is organized as:
1. `<head>` — CSS custom properties (design tokens), all CSS styles
2. `<body>` — One-page scroller with sections: Hero → Products → About → Order Process → Gallery → Community → Contact → Footer
3. End of `<body>` — All JavaScript

### Design System (CSS Custom Properties)
Colors, fonts, and spacing are defined as CSS variables at the top of the `<style>` block. The palette is grey/silver/white luxury aesthetic. Change these variables to restyle the site globally.

### JavaScript Functionality
- **Navigation:** Scroll-state detection adds a class to the fixed header; mobile hamburger menu with overlay
- **Animations:** Intersection Observer API drives scroll-triggered reveal animations; respects `prefers-reduced-motion`
- **Hero:** Ken Burns effect on background image + parallax on scroll (35% coefficient)
- **Form:** Client-side validation for the contact form (name, email, message required)

### Responsive Breakpoints
- 900px — navigation collapses to hamburger, grid adjusts
- 768px, 580px, 480px — progressive layout simplification

## Product Context (from README)
- Products: hair serum, hair oil, eyebrow dye.
- Design intent: curated/limited product range
- Target layout: one-page scroller with anchor navigation
