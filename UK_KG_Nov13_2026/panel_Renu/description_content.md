
# Paper–Term Knowledge Graph:

### Query : El Niño AND biodiversity | Scientific literature corpus : 50

## [Link to the output graph](https://github.com/semanticClimate/outreach/blob/main/UK_KG_Nov13_2026/panel_Renu/output-KG-encyclopedia.html)

## [Script to make KG from encyclopedia](https://github.com/semanticClimate/encyclopedia/blob/renu/drawKG/build_KGencyclopedia.py)


**Aim:** link 45 research papers to 284 encyclopedia terms, and compare what the literature says with how the encyclopedia organises the same concepts.

## Key numbers
| | |
|---|---|
| Nodes | **329** (45 papers + 284 terms) |
| Edges | **931** (863 paper–term + 68 term–term) |
| Term mentions | **13,522** |
| Papers | 2025: 10 · 2026: 35 · 31 journals |
| Terms in only one paper | 148 (52%) |

## Methods

1. **Collect papers:** 50 open-access papers were downloaded from Europe PMC as full text (`fulltext.xml`) with their metadata (`eupmc_result.json`). 45 appear in the graph, and the other 5 matched none of the encyclopedia terms.
2. **Read the encyclopedia:** Each term and its Wikipedia link, plus the links between entries, were taken from the encyclopedia HTML.
3. **Clean the text:** Only the abstract and main text were searched. The reference list, acknowledgements and citation numbers were removed so bibliographies do not inflate counts.
4. **Match terms:** Each term was searched in each paper as a whole word, ignoring capitalisation and allowing plurals. Short all-capital terms such as ENSO must match exactly.
5. **Build the graph:** An edge joins a paper to a term, with the number of mentions as its weight. A second set of edges joins two terms when one entry links to the other.
6. **Lay it out:** Positions are calculated once, so nothing moves. Papers sit on a ring, with similar papers next to each other. Terms shared by two or more papers sit inside the ring, and single-paper terms sit just outside their paper.

## How to read it
- **Gray cards** = papers · **dots** = terms
- **Dot size** = mentions in the whole corpus · **colour** = number of papers
- **Solid line** = paper mentions term · **dashed pink** = encyclopedia link
- Click a paper to see its terms sized by mentions in that paper

## Software
Python 3 · BeautifulSoup4 + lxml · NetworkX · NumPy · PyVis · vis-network (JavaScript) · Europe PMC · Wikipedia API

## Findings
- **Top terms:** temperature (642 mentions, 36 papers), rainfall (542), El Niño (463), population (449)
- **Frequent ≠ widespread:** one paper holds 83% of the rainfall mentions
- **Specialist topics:** snow depth and Postelsia are heavily used in a single paper each
- **Encyclopedia vs literature:** 44 of 68 term links also appear together in papers; 24 never do (possible gaps)


