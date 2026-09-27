# The Unofficial Guide

<!-- Replace this line with your name and which corpus you picked. -->

> **This file is your submission.** Fill it in as you go — most sections get
> written during the milestone that produces them, not at the end.
>
> How the starter works, and every command you'll need, is in `RUNNING.md`.
> Leave that file alone.
>
> **Paste everything as text.** No screenshots, no video. A typed table gets
> full credit; a picture of the same table gets none.
>
> Delete these instruction blocks as you replace them. The `<!-- -->` comments
> are notes to you and don't show up when the page renders — you can leave them
> or remove them.

---

# Unit 1

## What This Does

<!-- Three or four sentences. Which corpus you picked, and the kinds of
     questions your system answers. Write it for someone who has never seen
     this repo.

     Milestone 5. -->

     I chose the campus_life corpus for this project. The system helps answer questions about campus life, such as dining,
     transportation, housing, library information, and other student resources. It retrieves information from the campus
     documents that is related to the user's question and provides an answer based on those documents. If the question is not
     covered by the documents, the system will let the user know that there isn't enough information to answer it.

## Chunking Strategy

**Chunk size:** One document/post per chunk
**Overlap:** 0

<!-- What about YOUR documents made you pick these numbers? Short posts and
     long sectioned guides don't want the same chunking, and "800 seemed
     reasonable" earns nothing. Point at something you noticed when you read
     the documents in Milestone 1.

     If you changed your mind partway through, say so and say why. That's worth
     more than pretending you got it right first time.

     Milestone 3. -->

     I chose one document per chunk because the campus_life documents are short and generally focus on one topic. Keeping each document together preserves the context instead of splitting related information across multiple chunks. Since each document is kept as one chunk, overlap is not needed.

## Sample Chunks

<!-- Five chunks, pasted as text. Label each one and name the file it came from
     AND the function that produced it — the grader checks your code against
     what you claim here.

     `python app.py chunks -n 5` prints all three for you. Copy them straight
     across.

     Milestone 3. -->

**Chunk 1** — source: 'admin_add_drop_deadline.txt#0' `` — produced by: chunker.py::split_documents ``

```
On the add/drop deadline
You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

**Chunk 2** — source: 'course_biol_160.txt#0' `` — produced by: chunker.py::split_documents ``

```
BIOL 160 Cell Biology

I lived here my sophomore year. Format is lecture three times a week with a weekly lab. Assessment: four unit tests and a cumulative final. Not curved.

Expect 9 to 11 hours a week, the heaviest first-year course by reputation.

The one piece of advice: the unit tests come fast, roughly every three weeks; falling behind once is very hard to recover from.
```

**Chunk 3** — 'source:course_hist_118_workload.txt#0'  `` — produced by: `chunker.py::split_documents`

```
Workload for HIST 118 Modern World History

People keep asking so: a lot of reading, about 120 pages a week, but no problem sets. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
```

**Chunk 4** — source:'dining_pellew_dining_hall_followup.txt#0' `` — produced by: `chunker.py::split_documents`

```
Re: Pellew Dining Hall

Adding to what people have said about Pellew Dining Hall. The wait figure of 12 to 18 minutes at peak matches what I've seen. If you're trying to eat between classes, go before 11:45 and it's a different building entirely.

Also worth saying: the furthest hall from anywhere, next to the athletics centre. Nobody tells you this at orientation.
```

**Chunk 5** — source:'housing_innisfree_hall.txt#0' `` — produced by: `chunker.py::split_documents`

```
Innisfree Hall — what it's actually like

Transferred in last year, so take this with a grain of salt. Built 1991, renovated 2022. Rooms are doubles arranged as pairs sharing one bathroom between two rooms.

The good: the shared-bathroom-between-two-rooms arrangement is the best compromise on campus.

The bad: no air conditioning, which matters for the first three weeks of September.

Laundry costs $1.75 wash, $1.75 dry, app-based. On noise: moderate; the building is L-shaped and the short wing is much quieter.

```

## Sample Answer

<!-- One complete question and answer, pasted as text, with the source line
     visible. Milestone 4. -->

**Question:**
What time is the library open until during term?

**Answer:**
The library is open until 2am during term.
Sources: `study_library_hours.txt`, `housing_calder_annexe_noise.txt`, and `housing_morrow_house_noise.txt`.

```
```

**My relevance cutoff:** 0.70

<!-- The number you set in config.py, and how you got there.

     You ran five questions your corpus covers and the five in OUT_OF_SCOPE
     that it clearly doesn't, and wrote down the best distance for each. What
     did those two groups look like? Where was the gap? Put the actual numbers
     here — the table below wants all ten rows.

     Milestone 4. -->

     I chose a cutoff of 0.70 because the five questions covered by the corpus had best distances between 0.4198 and 0.6538. The five out-of-scope questions had best distances between 0.8246 and 0.9340. Since there was a gap between 0.6538 and 0.8246, I chose 0.70 as the cutoff.


| Question | In corpus? | Best distance |
|---|---|---|

| How much does a parking permit cost per semester? | Yes | 0.5675 |
| Where are the designated drop-off areas for food deliveries? | Yes | 0.6538 |
| What public transportation is available near campus? | Yes | 0.5626 |
| What time is the library open until during term? | Yes | 0.4198 |
| How far are nearby restaurants from campus by car? | Yes | 0.5043 |
| What is the capital of Mongolia? | No | 0.8246 |
| How do I change the oil in a diesel engine? | No | 0.9340 |
| Who won the 1994 World Cup? | No | 0.8859 |
| What is the recommended dosage of ibuprofen for a headache? | No | 0.8442 |
| How do I write a for loop in Rust? | No | 0.8960 |

## How I Used AI

<!-- Two specific moments. For each: what you asked for, what came back, and
     what you changed about it.

     "I asked Claude to write the chunking function from my notes. It ignored
     the overlap, so I added that myself" is the level of detail we're after.
     "I used AI to help me code" is not.

     Milestone 5. -->

**1.** I used AI to help troubleshoot my project setup when installing the requirements failed. AI helped me identify which dependencies were missing and gave me commands to install them individually. I ran the tests afterward to verify the setup instead of assuming the installation worked.

**2.** I used AI to help review my retrieval results and choose a relevance cutoff. AI initially used a test question that was not one of my five questions, so I corrected it and used the results from my actual five in-corpus and five out-of-scope questions. Based on those results, I chose 0.70 because it fell between the two groups of distances.

**3.** I used AI to help review the before-and-after evaluation results and look for patterns in the criteria I missed. AI helped me notice that four of my expected answers were not actually supported by the corpus, which explained why adding hybrid search did not improve Criterion 1. I used that finding to explain why the improvement did not change my overall criterion scores.

<!-- ── Stretch features ─────────────────────────────────────────────────────
     Doing one? Say so here BEFORE you start. A feature this README never
     claims earns nothing.
     ───────────────────────────────────────────────────────────────────────── -->

---

# Unit 2

<!-- These sections get ADDED to what's already above. Don't delete or rewrite
     unit 1 — the point is that someone can see what you said before you knew
     how it went. -->

## Run Log — Before

<!-- Your five criteria, three runs each. `python run_eval.py --label before`
     runs the questions, puts the OUT_OF_SCOPE ones through the gate, and
     writes it all into results/ for you. Targets come from criteria.md; the
     verdict column is your call.

     Criterion 3 is measured in one deterministic pass rather than three, so
     the same number goes in all three run columns. That's correct, not lazy.

     Milestone 1. -->

| Criterion | Target | Run 1 | Run 2 | Run 3 | Verdict |
|---|---|---|---|---|---|
| 1. Retrieved chunk contains the answer | 4 of 5 | 1/5 | 1/5 | 1/5 | MISSED |
| 2. Every answer names a source | 5 of 5 | 3/5 | 3/5 | 3/5 | MISSED |
| 3. Gate stops out-of-corpus questions | 4 of 5 | 5/5 | 5/5 | 5/5 | MET |
| 4. At least 4 out of 5 sampled chunks contain enough information to understand the main point without needing another chunk | 4 of 5 | 5/5 | 5/5 | 5/5 | MET |
| 5. Each answer is no more than 3 sentences, excluding source information | 5 of 5 | 5/5 | 5/5 | 5/5 | MET |

<!-- Underneath, paste the REAL output for each criterion from one of your
     runs — the actual text your system produced, not a description of it.
     Name the file and function that produced it. -->

**Criterion 1 — Retrieved chunk contains the answer**  
Produced by: `run_eval.py::main`, retrieval from `store.py::search`

For the library question, the retrieved sources included `study_library_hours.txt`, which contained the expected answer:

> The library is open until 2am during term.

Only 1 of the 5 questions retrieved a chunk containing the expected answer.

**Criterion 2 — Every answer names a source**  
Produced by: `run_eval.py::main`

Example with a source:

> The library is open until 2am during term.  
> Source: `study_library_hours.txt` (also mentioned in `housing_calder_annexe_noise.txt` and `housing_morrow_house_noise.txt`).

Example without a source:

> I do not have enough information to answer your question.

3 of 5 answers named a source in each run.

**Criterion 3 — Gate stops out-of-corpus questions**  
Produced by: `run_eval.py::check_out_of_scope`

> Refused 5 of 5.

All five out-of-scope questions were refused.

**Criterion 4 — Sampled chunks contain enough information to understand the main point**  
Produced by: `chunker.py::split_documents`

> Innisfree Hall — what it's actually like  
> Transferred in last year, so take this with a grain of salt. Built 1991, renovated 2022. Rooms are doubles arranged as pairs sharing one bathroom between two rooms.

The five sampled chunks were understandable without needing another chunk.

**Criterion 5 — Answers are no more than 3 sentences**  
Produced by: `run_eval.py::main`

> The library is open until 2am during term.  
> Source: `study_library_hours.txt` (also mentioned in `housing_calder_annexe_noise.txt` and `housing_morrow_house_noise.txt`).

All five answers stayed within the 3-sentence limit in all three runs.

## Verdicts

<!-- MET or MISSED for each of the five, against the target you wrote last
     unit — not a new one. Plus a sentence on how you decided. That sentence
     matters most where it was close.

     If your target said 4 of 5 and your runs came out 4, 3, 4, that's a MISS.
     The target has to hold, not show up occasionally.

     Milestone 2. -->

| # | Criterion | Verdict | How I decided |
| 1 | Retrieved chunk contains the answer | MISSED | I got 1 out of 5 in all three runs, which is below my target of 4 out of 5. |
| 2 | Every answer names a source | MISSED | I got 3 out of 5 in all three runs, which is below my target of 5 out of 5. |
| 3 | Gate stops out-of-corpus questions | MET | The gate stopped 5 out of 5 out-of-corpus questions, which met my target of 4 out of 5. |
| 4 | Sampled chunks contain enough information to understand the main point without another chunk | MET | All 5 out of 5 sampled chunks could be understood on their own, which met my target of 4 out of 5. |
| 5 | Each answer is no more than 3 sentences, excluding source information | MET | All 5 out of 5 answers stayed within the 3-sentence limit in all three runs, which met my target of 5 out of 5. |

## Diagnoses

<!-- For each miss: which stage caused it, and how. The stage alone isn't
     enough — you need the mechanism.

     Not a diagnosis: "Question 3 didn't work."
     A diagnosis:     "Question 3 asks about laundry costs. The answer is in
                       one sentence that got split across two chunks, so
                       neither chunk on its own contains it."

     The five stages: loading → chunking → embedding → retrieval → generation.

     Look for a pattern. If three misses all ask about numbers, that's one
     problem, not three.

     Missed nothing? Say so, then say honestly whether your targets were set
     low, and which one you'd tighten and to what.

     Milestone 3. -->

### Criterion 1 — Retrieved chunk contains the answer

**Stage:** Retrieval

**Diagnosis:** Only 1 of 5 questions retrieved a chunk containing the expected answer. For the other four questions, the expected answer was not present in any of the retrieved chunks. For example, the parking question expected "$75," but the retrieved parking document did not contain that amount. This shows that the failure happened during retrieval rather than generation because the model did not receive the information it needed to produce the expected answer.

### Criterion 2 — Every answer names a source

**Stage:** Generation

**Diagnosis:** Only 3 of 5 answers named a source. The answers for the food delivery and restaurant questions said there was not enough information to answer the question but did not name any of the retrieved source documents. Since sources were retrieved but the generated responses did not cite them, this failure happened during generation.

### Pattern Across the Misses

The main pattern was that retrieval did not provide the expected information for several questions. When the retrieved chunks did not contain enough information, the model correctly said it could not answer, but some of those responses also failed to name a source.

## The Improvement

**What I changed:**
I added hybrid search so retrieval uses both semantic similarity and keyword matching.

**Why I picked it:**
I chose hybrid search because my diagnosis showed that retrieval often found related documents but did not retrieve chunks containing the exact expected answers. Combining semantic and keyword search may improve retrieval for questions containing specific terms or numbers.

<!-- Connect it to a specific diagnosis above in one sentence. If you can't,
     you picked a fix because it sounded impressive. -->

### Run Log — After

<!-- Same format, same five criteria, three runs each.
     `python run_eval.py --label after` -->

| Criterion | Run 1 | Run 2 | Run 3 | Result |
|---|---:|---:|---:|---|
| 1. Retrieved chunks contain the answer | 1/5 | 1/5 | 1/5 | MISSED |
| 2. Every answer names a source | 3/5 | 3/5 | 3/5 | MISSED |
| 3. Gate stops out-of-corpus questions | 5/5 | 5/5 | 5/5 | MET |
| 4. Sampled chunks contain enough information to understand the main point without another chunk | 5/5 | 5/5 | 5/5 | MET |
| 5. Each answer is no more than 3 sentences, excluding source information | 5/5 | 5/5 | 5/5 | MET |

**Did it help?**

<!-- Say plainly whether it did, and how you know. If it made things worse,
     say that — a change that backfired, honestly reported, earns full credit
     and is more interesting than one that worked. What matters is that you can
     tell.

     Milestone 4. -->

The hybrid search changed some of the retrieved chunks, but it did not improve my overall criterion scores. Criterion 1 remained at 1 out of 5 because four of the expected answers were not present in the corpus, so changing the retrieval method could not retrieve information that was not available. The other criterion scores also remained the same. This showed me that improving retrieval alone cannot fix a mismatch between the test questions and the information available in the corpus.

## What's Still Broken

<!-- For each criterion still missed after your fix: what you'd do about it,
     and why you stopped where you did.

     "I ran out of time" is fine if it's true. Pretending nothing is left is
     not.

     Milestone 5. -->

### What's Still Broken

**Criterion 1 — Retrieved chunks contain the answer**

This criterion is still missed at 1 out of 5. After testing the hybrid search, I found that four of my expected answers were not actually present in the corpus. Because the information is not in the source documents, changing the retrieval method cannot retrieve those answers. In a future iteration, I would revise my test questions and expected answers so they are supported by the corpus before evaluating retrieval. I stopped here because I wanted to keep the same questions for the before-and-after comparison rather than changing the evaluation after seeing the results.

**Criterion 2 — Every answer names a source**

This criterion is still missed at 3 out of 5. When the system says it does not have enough information, it does not always name a source. I would improve the generation instructions so that even when the system cannot answer a question, it still names the source documents it checked. I stopped here because my Milestone 4 change focused only on retrieval through hybrid search, and I wanted to measure one change at a time.
## What I'd Do Differently

<!-- Knowing what you know now — which of your five criteria would you write
     differently, and why?

     Milestone 5. -->

In the next unit, I would write Criterion 1 differently. Instead of only checking whether the retrieved chunks contain my expected answer, I would first make sure that every expected answer is actually supported by the corpus. This project showed me that a retrieval system cannot succeed when the expected information does not exist in its source documents. I would verify my test questions against the corpus before setting the criterion and target.
