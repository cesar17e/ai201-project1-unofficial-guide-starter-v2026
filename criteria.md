# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## 1. Retrieved chunks contain the answer

For at least 4 of my 5 test questions, the retrieved chunks include one that
contains the answer.

**Why this target:**
The `campus_life` documents are short and usually focus on one specific topic, and each of my five questions asks about information directly stated in the corpus. I chose 4 of 5 because retrieval should find the correct single topic document most of the time while still allowing one difficult query.

---

## 2. Every answer names a source

Every answer the system produces names at least one source document.

**Why this target:**
Every generated answer is based on chunks retrieved from documents that already have a source metadata. Since the pipeline has the source available when generating an answer, I expect all answers it produces to name at least one source rather than accepting occasional unsourced answers.

---

## 3. The relevance gate stops out-of-corpus questions

When I ask a question my documents clearly don't cover, the relevance gate
stops it and the system returns "I don't have enough information about that" —
in at least 4 of 5 tries.

**Why this target:**
The five out-of-scope questions are intentionally unrelated to the `campus_life` corpus, so the relevance gate should reject most of them.
I chose 4 of 5 because embedding similarity can still produce an accidental close match even when a question is unrelated to the corpus.

---

## 4. Something about your chunks

All 5 of 5 sampled chunks should contain complete sentences without beginning or ending in the middle of a sentence.
     
**Why this target:**
The `campus_life` documents are short, averaging about 317 characters, and most contain only a few related sentences. Because the documents are already small, I expect the chunker to preserve complete sentences rather than splitting them in the middle.

---

## 5. Your choice

All 5 in-scope questions in `questions.py` should pass the relevance gate and reach answer generation.

**Why this target:**
Each of the five in-scope questions asks about information directly present in the campus_life corpus. Since the relevance gate is meant to block unsupported questions, I expect all five supported questions to pass the gate and reach answer generation.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
