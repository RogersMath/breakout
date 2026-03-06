# Here is the Prompt Used to Create This Project.

The prompt itself was created by Copilot after I wasn't happy with the first project and told it to make a prompt of what we're trying to do.







    You are a senior front‑end engineer and accessibility specialist. 
    Generate a single, self‑contained **index.html** file (no external assets, no build tools, no frameworks) 
    that implements a simple **Breakout‑style grammar game** with the following requirements.

    ========================================
    PROJECT OVERVIEW
    ========================================
    Title: “Grammar Breakout — Light Theme (WCAG‑A)”
    Audience: Introductory college‑level English grammar students.
    Goal: Each **correct answer** to a grammar puzzle **launches one ball** into a simplified Breakout game.
    Scope: Proof of concept to run offline in any modern desktop/mobile browser.

    ========================================
    DELIVERABLE
    ========================================
    - Output a **single HTML document** with inline `<style>` and `<script>`.
    - Do NOT include any commentary outside the code block.
    - Use only vanilla HTML/CSS/JS. No external fonts, images, libraries, or network calls.

    ========================================
    UI LAYOUT & THEME (LIGHT‑ONLY)
    ========================================
    - Use a **single, consistent light theme** for *all* surfaces (page, header, panels, modal, and **canvas**). 
      No dark mode, no automatic theme switching, no mixed light/dark.
    - Color tokens (use CSS variables in `:root`):
      --bg: #FFFFFF;          /* page background */
      --panel: #F5F7FA;       /* cards/panels */
      --panel-border: #CBD5E1;
      --text: #0B121A;        /* primary text (dark) */
      --muted: #334155;       /* secondary text (dark) */
      --accent: #0B57D0;      /* primary button */
      --accent-hover: #0A47AD;
      --focus: #1D4ED8;
      --error: #B00020;
      --ok: #0F9D58;
      --canvas-bg: #FAFBFD;   /* game field background (light) */
      --canvas-grid: #E5E7EB;
      --canvas-hud: rgba(0,0,0,0.06);
      --paddle: #111827;      /* dark game pieces for strong contrast */
      --ball:   #111827;
      --brick-1: #374151;     /* dark slate */
      --brick-2: #0B57D0;     /* dark blue */
      --brick-3: #7C2D12;     /* dark brown-red */
      --brick-4: #065F46;     /* dark green */
    - Ensure **high contrast**:
      - Text on panels: ≥ 7:1 (use the tokens above).
      - Dark bricks/paddle/ball on the light canvas: ≥ 7:1.
    - Structure:
      - Header with HUD badges (Level, Score, Accuracy) and controls (New game, Pause, Mute).
      - Main grid: left = game canvas in a panel; right = “Grammar Puzzle” panel with CTA button.
      - Stats panel below (Bricks cleared, Questions answered, Correct, Accuracy).
      - Footer with brief accessibility note.

    ========================================
    ACCESSIBILITY (WCAG 2.1 A)
    ========================================
    - Use semantic landmarks (`header`, `main`, `footer`, `nav`, `aside`) and clear heading hierarchy.
    - **Keyboard support**: 
      - Paddle: ArrowLeft/ArrowRight and A/D.
      - Enter submits an answer in the question modal; Esc closes it.
      - P toggles Pause; M toggles Mute.
    - **Focus management**:
      - Use `<dialog>` for the question modal.
      - When opening the modal, focus the first input.
      - On close, return focus to the question CTA button.
      - Visible focus ring using the `--focus` token.
    - **Live regions**:
      - A visually hidden `aria-live="polite"` node for announcements 
        (e.g., “Correct. Ball launched.”, “Game paused.”).
      - HUD changes are discernible; question feedback uses `aria-live`.
    - **No time limit on questions**: When the modal is open, pause the game loop.
    - Buttons use `aria-pressed` where appropriate; labels and descriptions for clarity.

    ========================================
    GAME MECHANICS
    ========================================
    - Canvas: responsive, crisp with DPR scaling; fixed aspect ratio 16:9; **fill the canvas each frame** with `--canvas-bg`.
    - Simplified Breakout:
      - One paddle, 1‑hit bricks, simple wall/paddle collisions.
      - Ball reflects with a gentle angle based on hit position on paddle.
      - No power‑ups, no spin, no complex physics.
    - **Firing mechanism**: 
      - A **CTA button** “Answer a question to fire a ball” opens the modal.
      - On **correct** answer: increment score (+50), **launch exactly one ball** from the paddle center.
      - On incorrect: feedback only; do not launch; no life loss.
    - Difficulty ramp by level:
      - Level 1: easy speed, fewer rows/cols, wider paddle.
      - Each new level slightly increases rows/cols and ball speed, and narrows the paddle a bit.
      - When all bricks in a level are cleared, automatically start the next level and announce it.
    - Scoring:
      - +10 per brick destroyed.
      - HUD shows Level, Score, Accuracy; stats panel shows Bricks cleared, Questions answered, Correct, Accuracy.

    ========================================
    QUESTION SYSTEM
    ========================================
    - Include a small **built‑in multiple‑choice** bank (15–20 items) suitable for intro college English grammar:
      - Topics: articles, subject–verb agreement, pronoun case/agreement, basic tense, fragments/run‑ons/parallelism.
      - Tag each item with a simple difficulty (1 easy, 2 moderate, 3 slightly harder).
    - Per level, randomly draw ~5 items with a cap on max difficulty for that level 
      (e.g., L1 uses d=1, L2 uses d≤2, L3+ uses d≤3).
    - Modal behavior:
      - Radio buttons for choices, large click/tap targets.
      - Immediate feedback text (“Correct! Launching a ball…”, “Not quite. Try the next one.”).
      - Enter submits; Esc closes; closing returns focus to the CTA.

    ========================================
    CONTROLS & AUDIO
    ========================================
    - Implement Pause (button + “P”) and Mute (button + “M”).
    - Tiny WebAudio “beeps” for wall/paddle/brick impacts and ball loss; respect Muted state.
    - Ensure AudioContext resumes on first user interaction (autoplay policy).

    ========================================
    IMPLEMENTATION NOTES
    ========================================
    - Use CSS variables for all colors; **do not implement a dark theme** and do not auto‑switch via `prefers-color-scheme`.
    - Ensure the canvas draws with **light background** every frame; remove any dark‑canvas remnants.
    - Keep code organized with clear sections: utilities/state, bank, modal, game core, loop/draw, bootstrap.
    - No analytics, no storage, no network, no SCORM—pure local runtime.
    - Make the code easy to extend (e.g., a function that returns questions for a level).

    ========================================
    DEFINITION OF DONE
    ========================================
    - The output is a single HTML file that runs when opened locally.
    - All surfaces are light; all text and game elements are dark; contrast is consistently high.
    - Keyboard controls, focus management, and live announcements function as described.
    - Answering a question correctly reliably launches one ball; levels advance when bricks are cleared.
    - No external dependencies and no console errors.

    IMPORTANT: Return ONLY one fenced code block containing the complete HTML document.

