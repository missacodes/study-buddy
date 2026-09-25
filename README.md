# Problem
When a student gets a maths question wrong, most quiz apps simply say "wrong, try again." This leaves them to guess where they went wrong. This app diagnoses the specific mistake behind a wrong answer and gives the user a hint pointing to that mistake.

# Scope
v1 covers one GCSE subject, which is maths, one topic, which is solving quadratic equations, and one method, which is factoring. Every question is already presented in the form x² + bx + c = 0, so the user doesn't need to rearrange.

# User flow
1. The student opens the app and is asked "how many questions would you like to solve?"
2. When the student chooses, they are shown a question and type their answer using a plain number pad.
3. If the answer is correct, they move on to the next question automatically.
4. If the answer is incorrect, a pop-up appears saying "Wrong, try again," along with a hint button — which only appears if a specific hint applies — and an option to skip.

# Adaptive behaviour
v1 diagnoses two failure modes from the submitted answer alone:
- **Sign error**: correct magnitudes, wrong +/− (e.g. submitting x = 2, 3 instead of x = −2, −3).
- **Stops at one root**: only one value submitted where two are required (e.g. x = −2 alone).

A third, common failure mode is wrong factor pair. It can't be reliably diagnosed from the final answer alone — indistinguishable from a random guess — so it falls back to the "wrong, try again" message with no specific hint.

# Non-goals
**Deferred:** LangGraph adaptive agent, RAG over revision notes, voice input (AssemblyAI), Supabase auth + progress tracking, Next.js frontend.

**Cut for v1:**
- Other forms of solving quadratics, such as the quadratic formula, completing the square, or the graphical method — factoring only, to keep the diagnostic logic to one method.
- Photo/OCR input of handwritten working — cut because it would require OCR plus vision-model infrastructure, too large for a scoped-down v1.
