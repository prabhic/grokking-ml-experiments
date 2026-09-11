# Playground conventions

Use `linear-regression-lab.html` as the canonical visual and interaction reference for all playgrounds. Inspect it before creating or redesigning a lab.

- Put the interactive workspace first, with a sticky, compact top toolbar grouping the relevant controls.
- Use a large primary visualization and a narrower right rail for related views, numerical readouts, and a trace of the current calculation or action.
- Place numbered mechanism stages directly beneath the primary visualization, reflecting the current state where useful.
- Put the extended explanation below the workspace: an editorial heading, a short introduction, and notes covering how to read the visualization, the calculation, controls, terminology, and concrete experiments to try.
- Match the reference's blue-gray graph-paper background, near-white panels, thin borders, 3px corners, teal/rose/gold accents, Fraunces headings, IBM Plex Sans body, and IBM Plex Mono controls/readouts. Provide fallback fonts.
- Preserve the responsive pattern: horizontally scrollable toolbar, stacked visualization/rail at narrower widths, and readable mobile panels. Label controls, expose selected button states, and preserve keyboard focus visibility.
- Keep each playground a standalone HTML file with no build step or runtime JavaScript dependencies. Explain teaching-data assumptions and mathematical edge cases clearly.

Adapt the controls and mechanism stages to the subject; the reference's training controls are specific to linear regression.

## Teaching principles

- Every important claim should be playable. Give the learner a control that changes the mechanism and a visible result that changes because of it.
- Use a concrete numerical example before introducing terminology. Show the operation on small vectors, not only in prose.
- Make the hidden bridge explicit. If a concept requires a conversion (for example, index → vector), give that conversion its own visual stage and interaction.
- Keep each playground focused on one mechanism. A sentence, note, or formula can explain the mechanism, but it should not substitute for an experiment.
- Show both the learner's action and the model's resulting representation. Prefer before/after values, traces, and matched examples over declarative summaries.
- Distinguish what is fixed, what is looked up, what is calculated, and what is learned. Label those roles in the interface.
- Add a worked edge case when a common intuition can fail. State toy-data limits beside the visualization.
- A slider is not enough: the control must correspond to a named quantity in the mechanism, and the readout must show the intermediate numbers that causally produce the result. Avoid decorative bars or generic “input → output” copy.
- Let the learner reproduce a before/after discovery: begin with a concrete toy state, change one thing, and make the changed operation and changed representation visible together.
- Include a brief “A short history” note in the bottom description of every playground. Identify the important originators or landmark work when the attribution is known, distinguish the historical idea from the modern LLM implementation, and link to a trustworthy primary source when practical. Keep history below the experiment so it enriches context without replacing the playable explanation.
- Use the Georgia Tech [Transformer Explainer](https://poloclub.github.io/transformer-explainer/) as a reference for connected visual explanations: start with a concrete text/prompt, let the learner expand the pipeline progressively, keep token-level views linked to matrix/vector views, update numerical values live, and make hover/selection/highlighting reveal relationships.
- When a concept belongs to a larger pipeline, show its upstream input and downstream consequence in the same workspace. For transformer concepts, preserve the chain `text → tokens → embeddings + positions → Q/K/V → scores → mask → softmax → weighted values → MLP/residual → logits → probabilities → sampling` where the playground scope permits.
- Separate cross-token communication from per-token transformation: attention routes information between tokens; the MLP/feed-forward stage transforms each token independently. Do not collapse these into one generic “transform” label.
