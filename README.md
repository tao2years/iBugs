# Dataset - iBugs

This is the dataset for the ISSTA`22 submission "Understanding Device
Integration Bugs in Smart Home System". It contains 330 device
integration bugs collected from the most popular open source SmartHome
system, i.e., Home Assistant. 

## Getting started 
You can directly use the dataset for further analysis, including bug
detection, bug fix, etc. All details are showed in the file.

## Detailed description
The document shows the final result after iterative labeling process
by 4 authors, including 7 columns:
- Issue ID. Indicate the issue where the bug was identified.
  Considering the issue
  (https://github.com/home-assistant/core/issues/43173), we record
  *43173* in this column.
- Integration. Indicate the device integration where the bug occurred. 
- Taxonomy. The taxonomy of the root cause. Specifically, in this
  article, it represents the corresponding life cycle stage, e.g.,
  discovery process, initialization process, execution process.
- Root cause. The atomic categories of root causes. 
- Fix. Brief descriptions of fix patterns.
- Impact. Impacts that iBugs can lead to.
- Trigger. Types of trigger conditions.


## How did we construct the dataset?
**Data collection.** We manually went through issues and pull requests
(PRs) of the Home Assistant repository [1] on GitHub to collect iBugs.
First, we concentrated on the closed bug reports with the label
``integration'', the number of which is larger than ten thousand.
Second, we selected issues in the second half of 2020
(2020.5-2020.12). Next, we searched for each issue's associated merged
pull request, which indicated that the issue was potentially a real
bug. Then we manually read the issue report and discussions to screen
out iBugs. 

**Data analysis.** The collected GitHub issues were manually analyzed
by four authors following an open coding procedure [2]. We created a
shared document containing five columns, i.e., issue ID, root cause,
fix, impact, trigger. The authors need to label the last four columns.
To explore the root causes of iBugs, we tried to answer the question
``what caused this bug at the code level''. Based on the stack traces
and messages in the issue reports, we located the buggy code and
figured out what caused the bugs. The fixes were obtained from the
associated pull requests, and finally, we manually extracted the
common patterns by abstracting the patches. The impacts and trigger
conditions can be inferred by issue reports straightforwardly. 

Each author independently labeled the document assigned to him by
defining the range of issue IDs. The shared document can show all the
created labels during the labeling process, and all authors can
further use them. Such a choice can help us use consistent naming
without introducing bias. Authors also discarded issues and PRs that
can not represent a bug or be fully understood. 

The labeling process is conducted iteratively. In each round, the
authors discussed the problems they met. After each labeling
iteration, all potential conflicts between authors were resolved. We
continued this process until the labels reached a state of saturation
where no new label appeared after three rounds. 

**Taxonomy construction.** We used a bottom-up approach [3] to
construct the taxonomy. We first grouped the bugs according to the
different dimensions based on the proposed integration model. Then we
grouped labels that correspond to similar views into categories. After
that, we constructed parent categories to extract common features
further. Each sub-category should belong to its parent category. The
whole process was discussed and decided by all authors through offline
meetings. 


## Reference
[1] Home Assistant repository. https://github.com/home-assistant/core

[2] Carolyn B. Seaman. 1999. Qualitative Methods in Empirical Studies
of Software Engineering. IEEE Transactions Software Engineering 25, 4
(1999), 557–572.

[3] Vijayaraghavan Giri and Cem Kaner. 2003. Bug Taxonomies: Use them
to Generate Better Tests. In Software Testing Analysis and Review.
1–40.

