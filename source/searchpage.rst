.. _searchpage:

Searching the Reports
=====================

Use the search page to query the full-text database and find reports.

Match any term
  wilde verdict matches "wilde" or "verdict."

Wildcards
  crim* matches "crime" and "criminal".

  s?t matches "sit" and "sat" but not "saat."

Match all terms
  +wilde +verdict matches paragraphs which contain both wilde and verdict.

Exclude some terms
  -wilde +verdict matches paragraphs which do not contain wilde but do
  contain verdict.

Phrase searches
  "at the witness box"

Proximity search
  "wilde queensberry"~10 matches paragraphs which contain the words
  wilde and queensberry no more than 10 words apart.

Fuzzy search
  persecution~ matches words which are similar to
  persecution. persecution~0.9 matches words which are closer to
  persecution than persecution~0.1 would.

Booleans
  queensberry AND clarke finds paragraphs that contain both queensberry and clarke

Grouping booleans
  (queensberry OR wilde) AND clarke
