
# What the Graph Shows

### Query : El Niño AND biodiversity

## [Link to the graph]()

It is one network with two layers on the same set of terms:

- **Paper–term layer:** Which of the 45 papers mention which encyclopedia terms. Solid lines.
- **Term–term layer:** Which terms the encyclopedia itself cross-references to each other. Dashed pink lines.

Putting both layers together lets you compare what the literature says (papers) with how a reference source organises the same concepts (the encyclopedia).

## Statistics

| Item | Value |
|---|---|
| Nodes | **329** (45 papers + 284 terms) |
| Edges | **931** = 863 paper–term + 68 term–term |
| Term mentions counted | 13,522 |
| Paper–term layer | Bipartite (verified) |
| Whole graph | One connected network (not bipartite, because terms link to terms) |
| Papers | 10 from 2025, 35 from 2026, 31 different journals |
| Average per paper | 19 terms (range 5–34) |
| Average per term | 3.0 papers |
| Terms in only one paper | 148 (52%) |
| Terms in 10 or more papers | 15 |
| Terms with a term–term link | 70 of 284 (25%) |
| Term–term clusters | 14 (one large group of 33 terms, 13 small groups of 2–5) |

## Methods

1. **Collect papers:** 50 open-access papers were downloaded from Europe PMC as full text (`fulltext.xml`) with their metadata (`eupmc_result.json`). 45 appear in the graph, and the other 5 matched none of the encyclopedia terms.
2. **Read the encyclopedia:** Each term and its Wikipedia link, plus the links between entries, were taken from the encyclopedia HTML.
3. **Clean the text:** Only the abstract and main text were searched. The reference list, acknowledgements and citation numbers were removed so bibliographies do not inflate counts.
4. **Match terms:** Each term was searched in each paper as a whole word, ignoring capitalisation and allowing plurals. Short all-capital terms such as ENSO must match exactly.
5. **Build the graph:** An edge joins a paper to a term, with the number of mentions as its weight. A second set of edges joins two terms when one entry links to the other.
6. **Lay it out:** Positions are calculated once, so nothing moves. Papers sit on a ring, with similar papers next to each other. Terms shared by two or more papers sit inside the ring, and single-paper terms sit just outside their paper.

## How to Read It

- **Gray cards:** Papers, labelled “Author Year”. A card is slightly larger when the paper covers more terms.
- **Dots:** Terms, coloured by how many papers mention them: green for more than 15 papers, blue for 9–15, orange for 4–8, and gray for 3 or fewer. Dot size follows the same count.
- **Solid cyan lines:** A paper mentions a term, and a thicker line means more mentions.
- **Dashed pink lines:** The encyclopedia links the two terms.
- **Interaction:** Clicking a node shows only its direct neighbours. Hovering shows the Wikipedia summary for terms, and the title, authors, journal and DOI for papers, with a ↗ link to the source.

## Software

- **Language:** Python 3.
- **Libraries:** BeautifulSoup4 with lxml (reading the HTML and XML), NetworkX (graph building, checks, layout and statistics), NumPy (layout), PyVis (the interactive page), and vis-network 9.1.2 in JavaScript (drawing in the browser).
- **Other sources:** The Wikipedia REST API for term summaries, and Europe PMC for the papers.

## What the Graph Tells Us

1. **A shared core vocabulary:** *temperature* appears in 36 of 45 papers and *El Niño* in 33, followed by *distribution* and *population* (28 each). These terms tie the whole collection together.
2. **The encyclopedia and the papers mostly agree:** 44 of the 68 term links (65%) also appear together in at least one paper. The strongest are *precipitation* with *rainfall* (10 papers together), *biodiversity* with *ecosystems* (7) and *El Niño* with *sea surface temperature* (4).
3. **Links the papers never use:** 24 encyclopedia links never appear together in any paper. Examples are *drought* with *extreme precipitation*, *biodiversity* with *marine ecosystems* and *sea surface temperature* with *marine heatwaves*. These could be relationships worth studying or places where the encyclopedia is ahead of the literature.
4. **The most discussed terms are the least cross-referenced:** *temperature* has only 2 term links, *El Niño* has 1, and *population*, *distribution*, *taxa* and *richness* have none. The encyclopedia could add links around these central terms.
5. **A biodiversity and geography cluster:** The largest term–term group has 33 terms. It joins *biodiversity*, *ecosystems*, *deforestation* and *habitat loss* with places (South America, Colombia, Brazil, Peru, the Amazon Basin and the hemispheres). *Biodiversity* has the most term links among the concept terms (7), and it is also in 19 papers. This group touches 41 of the 45 papers.
6. **Small topic groups:**
   - *drought*, *agriculture*, *food security*, *farmers* and *extreme precipitation*
   - *phytoplankton*, *cyanobacteria*, *macroalgae* and *plant species*
   - *El Niño*, *sea surface temperature* and *marine heatwaves*
7. **Specialist terms:** 148 terms appear in only one paper, such as *snow depth* and *Postelsia*. They are entry points to narrow subtopics.

## Who Benefits

- **Newcomers** see the main concepts and how they connect before reading.
- **Researchers** find papers on a topic and spot gaps.
- **Encyclopedia editors** find missing links and duplicate terms, such as the several El Niño variants.
