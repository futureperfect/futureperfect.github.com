# IBM Talk about Watson @ Georgia Tech

I went to a really interesting talk about IBM’s Watson by Bill
Murdock, a member of the Algorithms team (and fellow Georgia Tech
alum). The room was one of the largest lecture rooms the College of
Computing has access to and the interest was well beyond capacity.
Here are some notes I took of his presentation for those of you who
were unable to attend. He gave a pretty good explanation of some of
the more egregious snafus that happened during the course of the
tournament, including the Final Jeopardy question where it seemed to
indicate that it thought Toronto was a city in the US.

I think I was most surprised in the end by how much of Watson was
based on statistical reasoning over unstructured text documents, given
the problem domain naturally lends it self to symbolic reasoning and
inference techniques.

Notes
----

Speaker: Bill Murdock - IBM Research

Background
----------

DeepBlue defeating Gary Kasparov at chess was ~10 years ago
- important achievement in a complex problem domain

DeepQA is a very different problem:
- Chess - it was finite, well defined state can be encoded in a very compact
  representation
- Jeopardy - human language, context, ambiguity, grounded in human cognition

numerous ways express a conceptual question

Where was Einstein born?
- using structured data, easy
- unstructured text, hard
inference is a bitch, cut structuring your data is often an untenable
proposition

"Hard part for Watson is finding and justifying an answer and providing a
confidence"
People are extremely good at this, though

Jeopardy
--------

Top human players are really good. Winners win well over half the board.

Ken Jennings answers 60-70 percent of questions, 85% right consistently
DeepQA started off *much* worse. Got less than half of things it was most
confident about right. Typically less than 20% confident about any answer.

Big Idea
--------

- Deep Analysis - semantic analysis dictionaries, encyclopedia, web
- search for many answers based on different interpretations
- use many different NLP techniques and reasoning algorithms
- uses statistical analysis engine to rank answers based on confidence values
- rank based on confidence
- if top is above threshhold, buzz in, else keep your mouth shut

----
    big ass diagram of architecture here
----

1. Question analysis - parts of speech, grammatical relationships, probabilistic
   estimation of sort of question
1. is this a multipart question? if so, have to decompose question

Hypothesis generation:
- primary search
    - go find documents
    - text snippets
    - knowledge bases
    - statistical knowledge base based on word correlations
- candidate answer generation
  - look through results, find things that look like candidates
  - go through paragraphs and find potential answers (tied to answer type)

- Hypothesis and Evidence Scoring
  - surface answer scoring (characteristics of answer in isolation, no context
    e.g. several algorithms to find if answer is suitable answer type (is it a
    person? place? ))
  - evidence retrieval (do a secondary source based on particular answer
    candidate to see if there's anything that reinforces strength of answer)
  - How well do other passages support candidate answer?
- Deep evidence scoring

- Synthesis
  - assign confidence values
- Final confidence merging and ranking

__Presenter's Computer crashes here__

DeepBlue and DeepQA have very little in common
- different problem domains
- DeepQA not an exercise in pushing hardware whereas DeepBlue very much was
- new techniques, algorithms were what made Watson possible

Watson's information retrieval process was naturally very parallellizable
- evidence leads to candidate answers which leads to more evidence which leads
  to more candidate answers


DeepQA got WAY BETTER in the few years it was under development

Jeopardy is hard because of a need for precision, confidence, and speed

If you ran the DeepQA answer search process on single processor sequentially, it
would typically take ~2 hours

Over 2800 Power7 cores the process can be parallelized down to ~3 seconds

Hypothesis generation tends to be liberal in accepting candidate hypotheses for
exploration, choosing to let later stages of the pipeline remove answers rather
than dismissing them outright.


Business Applications
---------------------

- *Healthcare/life sciences*: DiagnosticAssitance, evidence-based collaborative
  medicine
- *tech support*: help desk, contact centers
- *Enterprise knowledge management and business intelligence*: companies with
  cast quantities of data, want to extract knowledge
- *government*: improved information sharing and education

Evidence profiles were diagnostic tools for evaluating what Watson did, but
jeopardy does not demand explanation of support. Other domains would perhaps be
more critical.

For example, healthcare applications would likely demand an explanation of why a
particular answer was given before accepting it

Medicine has a constantly updating corpus of information that may cause new
answers to be given for medical domain questions
- new drugs come to market
- new tests performed give new insight and data into a particular illness
- not a static corpus of data to work with

----

Really surprised we got this right:
($600) Literary character APB: Wanted for general evilness, last seen at the
tower of Barad-Dur; it's a giant eye, folks. Kinda hard to miss.

WATSON: "Sauron" (0.74) - CORRECT
4 independent clauses, lots of slang, not useful phrases (kinda, folks)
used tower of Barad-Dur to root search

----

($200) Name The Decade: Disneyland opens and The Peace Symbol is created
WATSON: "1950's"

did not solve problem by looking up db of events
    manual effort needed to create this
    only would work on narrow set of questions

Instead, organized information to concept "decade", had strong evidence that
1950's was a decade

Evidence profile shows `1950's` beating `Kingdom` on almost all dimensions - big
factors - *Document Support* and *Type Match*

----

($600) Olympic ODDITIES: A 1976 entrant in the "modern" this was kicked out for
wiring his epee to score points without touching his foe
WATSON: "Pentathalon" CORRECT

epee would suggest fencing, but modern suggest something else

a priori probability was much higher that fencing would be the answer compared
to pentathalon. passage support helped a lot

----

($1000) OLYMPIC ODDITIES: It was the anatomical oddity of US gymnast George
Eyser, who won a gold medal on the parallel bars in 1904
WATSON: leg (0.61) - WRONG! (Correct answer: "wooden leg")

very difficult to anticipate a concept like "oddity", we DO NOT build a database
ahead of time

found passage stating "George Eyser's left leg was made out of wood", but did not
understand which part was the "oddity"
did not understand oddity of leg versus the fact that it was wood

----

Literary Character APB: His victims include Charity Burbage, Mad Eye Moody and
Severus Snape; he'd be easier to catch if you'd just name him

Harry Potter - WRONG (correct answer: Lord Voldemort)

close call, voldemort was second strongest confidence
didn't understand that all elements in the category were bad guys
weak reference to Voldemort with no one saying his name was totally lost on us
victim and murderer is a relationship that DeepQA could understand

----

FINAL FRONTIERS: It's a 4-letter term for a type of summit; the first 3 letters
mean a type of simian

WATSON: Peak (0.65) - WRONG! (Correct Ans: Apex)

Matched first constraint, second constraint was not understood

*skip some questions*

----

DIALING FOR DIALECTS: Dialects of this language include Wu, Yue, and Hakka

Watson: Cantonese (0.41) - WRONG (Chinese)

Rare case where open domain type analysis hurts difference between dialect
versus language is subtle. 
Documents often refer to cantonese as a language

----

US Cities - Largest airport is named for a WWII hero; it's second largest, for a
WWII battle

Watson: Toronto (0.14) - WRONG Chicago

Toronto v chicago

one of the challenging issues is this clue asking for a US city?
for this clue, we do propose US City as the answer type with moderate confidence
(not extremely high)
Is Toronto a US city?
Go to db of entities, first hit was "Toronto the largest city in Canada"
lots of other smaller entities, e.g. band, couple of small cities in Iowa and
Ohio
lots of evidence that it was a city
list of fictional US presidents lists one being kidnapped in Toronto
List of US and Canadian Cities rare case where and is a union, meant or
(Note: Wikipedia kind of fucked Watson)
flaky and unreliable evidence
if it hadn't been final Jeopardy, Watson would not have answered.
would have worked reasonably well in different problem domain if Watson could
produce Evidence and answer set

Questions
---------

What did Bill work on?
Everything, but in particular answer scoring and deep evidence scoring

Very little is specific to Jeopardy, besides training based on previous games of
Jeopardy
some things (e.g. 4 letter word meaning X) would be of limited utility
most of it is still generalizable

what was the relative importance of ontologies?
Looked at OpenPSYCH (sp?)
Not particularly useful, some typing info for terms is available from this
corpus
Had lots of other typing sources, so not useful overall

Watson would have a chance to do much better at a large portion of the reasons
people use search engines currently, such as asking a question and desiring an
answer rather than a collection of potentially related documents.
