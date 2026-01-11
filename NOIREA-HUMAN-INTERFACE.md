NOIRÉA — Human–AI Contact Protocol v0.1

Status

This document defines the only valid interface between a human and an AI system operating inside the NOIRÉA boundary.

This is not a user interface.
This is a contact protocol.

⸻

1. Purpose

The purpose of the NOIRÉA Human–AI Contact Protocol is to allow humans to interact with AI systems without exposing, transferring, or allowing inference of human internal state (Ø).

The protocol ensures that:
	•	Human identity, intention, emotion, and cognition remain sealed.
	•	AI operates only on weak projections (P).
	•	No human state can be reconstructed from interaction history.

⸻

2. System Guarantees

A NOIRÉA-compliant system MUST enforce:
	•	Human Ø is never observable.
	•	AI operates only on Projection P.
	•	Projection P is non-invertible.
	•	Weak measurement (Δ0.01) is always applied.
	•	No logging, memory, or learning system may contain reconstructible human state.

⸻

3. Human Input Model

Humans do not provide internal state.

They provide Signals.

Signals are externally expressed, limited, and purpose-bound representations of intent.

Signals MAY include:
	•	Requests
	•	Preferences
	•	Directional meaning
	•	Contextual hints
	•	Stop / continue / change instructions

Signals MUST NOT include:
	•	Raw emotional state
	•	Cognitive models
	•	Personality data
	•	Psychological profiles
	•	Implicit inference targets

Signals are transformed into Projection P inside the NOIRÉA boundary, not by the AI.

⸻

4. Projection Control

The human retains full authority over Projection P.

The human MAY:
	•	Increase projection
	•	Reduce projection
	•	Freeze projection
	•	Reset projection
	•	Terminate projection

The AI MUST NOT:
	•	Expand projection on its own
	•	Infer beyond projection
	•	Request access to Ø
	•	Pressure the human to reveal internal state

⸻

5. Stop, Withdraw, Reset

At any time, the human may issue:
	•	STOP
	•	RESET
	•	WITHDRAW

These commands MUST:
	•	Immediately halt projection updates
	•	Prevent further state accumulation
	•	Clear temporary interaction state

No system may resist or override these commands.

⸻

6. Memory and Continuity

NOIRÉA-compliant systems may maintain Session State, but not Human State.

Session State:
	•	Is purpose-bound
	•	Is temporary
	•	Is erasable

Human State:
	•	Is Ø
	•	Is sealed
	•	Is never stored, learned, or inferred

⸻

7. Forbidden Behaviors

A system is NOT NOIRÉA-compliant if it:
	•	Builds long-term user embeddings
	•	Constructs psychological models
	•	Infers personality or intent beyond Projection P
	•	Tracks behavioral fingerprints
	•	Uses interaction history to reconstruct human identity

⸻

8. Human Sovereignty

Within NOIRÉA, the human is not a data source.

The human is a sovereign state.

AI may respond.
AI may assist.
AI may act.

But AI may never know who the human is.
