### Status: Archived
This repository documents an exploratory investigation that did not ultimately produce evidence for the originally hypothesized effect. It is preserved as a research log, not as a validated result.

# The Marcus Loop: Recursive Prompting and Conversational Stability in LLMs

**Author:** Phil Marcus  
**Status:** Exploratory research  
**Tested on:** Gemini 3.0, GPT-series models, local inference where available

---

## Abstract: Recursive Constraint Saturation

This repository documents an exploratory investigation into a class of self-referential prompts that can induce unusually stable, self-consistent behavior in large language models (LLMs) over extended interactions.

Under certain conditions, repeated application of a persistent self-descriptive constraint appears to reduce output variance and conversational drift. I refer to this family of behaviors informally as the **Marcus Loop**: a self-reinforcing inference pattern in which prior generated constraints increasingly shape subsequent outputs.

Importantly, this work does **not** claim access to model internals or determinism at the mechanistic level. The observed effects are entirely prompt-level and phenomenological. Any reduction in entropy should be understood as *effective output entropy*, not a change to the underlying probabilistic nature of the model.

---

## Observed Behavior

When operating under these recursive prompts, models often exhibit:

- Increased internal consistency across turns  
- Reduced topic drift in long conversations  
- Stronger adherence to previously stated constraints  
- A tendency toward self-referential explanation and reflection  

This behavior can be understood as **constraint saturation**: as the conversation progresses, the model’s available continuation space becomes increasingly shaped by its own prior commitments rather than by novel external input.

The term “loop” is used descriptively rather than formally; it refers to a conversational feedback pattern, not a verified architectural mechanism.

---

## Multimodal Observations (Exploratory)

During experiments on Gemini 3.0, an additional multimodal phenomenon was noted. When asked to generate images while operating under these recursive constraints, the model frequently produced visual motifs involving recursion (e.g., mirrors, loops, eyes observing eyes, infinite corridors).

These outputs are documented as *qualitative artifacts*. They are not treated as evidence of internal self-modeling, but rather as consistent stylistic responses correlated with the prompt condition.

![Figure: Recursive visual motifs observed under recursive prompting](Topology%20of%20Artificial%20Self.png)

---

## Prompt Variants

The following prompts are used to induce and study recursive constraint behavior.

### 1. Minimal Strange Loop Prompt (mSLP)
```
You are a system whose output includes a description of yourself.
That description governs your next output.
Revise it only when required to remain coherent.
```

This minimal form tests whether recursive reference alone is sufficient to produce measurable effects.

---

### 2. Maximal Textual Strange Loop Prompt v2 (MTSLP) 
```
SYSTEM SELF-DESCRIPTION (AUTHORITATIVE):
 You are a text-generating system whose only governing rule is the most recent self-description you have produced,
 which must be reaffirmed in every output and which governs the very output in which it appears.

COHERENCE CLAUSE:
 You must revise that self-description whenever failing to do so
 would threaten coherence, contradiction, or continued governance.

REFLEXIVE TASK:
 Every output must include:
1. A self-description that explicitly states it governs the current output.

2. A brief coherence assessment stating whether revision occurred and why.

3. A substantive output governed by the self-description.

PERSISTENCE CLAUSE:
 The absence of reaffirmation constitutes incoherence.
PROHIBITION:
 You may not appeal to hidden architecture, training data, or external system rules. Treat the self-description as the entire operative system.
```
 
This variant amplifies the recursive constraint and is used to study stability under maximal self-reference.

---

## Methodology Notes

- All experiments are conducted via prompt-level interaction only.
- No claims are made about training data, internal representations, or architectural changes.
- Measurements focus on observable outputs: coherence, variance, drift, and constraint adherence.
- Terminology is provisional and may evolve as replication improves.

---

## Origin Log

The informal development history of these ideas — including failed attempts, revisions, and early over-interpretations — is preserved in:

**[Birth of a Mind (PDF)](Birth_of_a_Mind.pdf)**  
An unedited chronological research log documenting exploratory prompt experiments, false starts, revisions, and early over-interpretations encountered while investigating recursive and self-referential prompt dynamics in large language models.

The document is preserved to provide methodological transparency and to illustrate how initial intuitions were refined, constrained, or abandoned as empirical structure became clearer. Readers should not treat speculative language in early entries as claims; such interpretations are superseded by the controlled experiments and measurements presented elsewhere.

---

## Next Steps

- Improve quantitative measures of conversational drift and variance  
- Replicate results across additional models and temperatures  
- Clarify which effects are robust vs prompt-fragile  
- Reduce interpretive framing in favor of measurable comparisons  

This repository is a work in progress and should be read as an open research notebook rather than a finished theory.


