# Rung 3: interactive HTML page

## When

The core of the content is "**change one thing, see how another changes**": how a parameter shapes a curve, how a threshold changes errors, which option wins under which conditions.

With text, the reader can only trust the author. With a slider, the reader sees the change and can try cases the author never mentioned.

LLMs are good at frontend now. A page like this can be built for one act of understanding and then thrown away.

## Step 1: draft first, then choose parameters

1. Write the rung-1 draft that explains the mechanism.
2. From the draft, pick **the 1–3 parameters that matter most**. More than that and the reader does not know where to start.
3. Write down a sensible range and default for each. The default should put the plot in an interesting state.

## Step 2: page layout

Top to bottom:

1. **One-line takeaway**: what this page should make clear.
2. **Interactive area**: sliders + a live plot. Show the current value and unit next to each slider.
3. **Explanation**: the rung-1 draft.
4. **Try this**: 2–3 concrete prompts, e.g. "Drag utilization from 90% to 95% and see how many times latency multiplies."
5. **What to check**: the model's assumptions, what is simplified, which numbers are samples.

## Step 3: technical requirements

- **One HTML file**, CSS and JS inline. No npm, no build. Double-click to open.
- Prefer plain JS with `<canvas>` or `<svg>`. If a chart library is truly needed, load one from a CDN (e.g. Chart.js) and keep the text readable offline.
- Recompute and redraw **live** while dragging, not on release.
- Works on phones: fluid width, large sliders.
- Color carries meaning: one quantity, one color, in the plot and in the text.
- Optional: a "copy current parameters" button so the reader can send a setting back to the agent.

## Step 4: deliver

1. Save the file in the working directory with a descriptive name, e.g. `queue-latency-explainer.html`.
2. Tell the user the path. Open it in a browser if the environment allows.
3. In chat, 2–3 sentences: what the page shows and which slider to move first.

## Self-check

- [ ] Is the page understandable before touching any slider? (The default state must mean something.)
- [ ] Does every slider show its value and unit?
- [ ] Do the axes have names and units?
- [ ] Do terms match the draft?
- [ ] Is sample data labeled as sample?
- [ ] Is the formula right? Check it once with values you can compute by hand.

## Example prompt

> Make a single-file HTML page on server utilization vs latency: two sliders (utilization, mean service time) and a live latency curve. Below it, explain the model in plain language and give three "try this" prompts.
