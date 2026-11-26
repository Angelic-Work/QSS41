# Twitch Social Network Analysis

**Does the language you stream in shape your success on Twitch?**

Final group project for a quantitative social science (QSS) course on the analysis of social networks, Dartmouth College. We analyzed a large Twitch social network to see how language shapes popularity, sponsorship, and connections between communities.

Materials: [`twitch_report_compiled_preview.pdf`](./twitch_report_compiled_preview.pdf) and [`QSS_PPT.pdf`](./QSS_PPT.pdf)

## Overview

Success on Twitch is usually credited to content quality and streaming frequency. We asked whether language also acts as a structural force, clustering users into communities and affecting who gets visibility. We focused on four non-English language communities: Spanish, French, Russian, and Chinese.

## Data

- **Source:** the Twitch Gamers Social Network dataset (Rozemberczki and Sarkar) from Stanford SNAP: 168,114 users and 6,797,557 mutual-follower edges, with attributes such as views, account lifetime, language, and affiliate status.
- **Pruning:** removed dead accounts and kept the four language communities, leaving 19,770 nodes and 323,741 edges.

## Questions and Methods

| Question | Approach |
| --- | --- |
| **Popularity:** can centrality identify popular streamers? | Compared degree and eigenvector centrality to view counts using top-100 overlap and Pearson correlation |
| **Power:** how does language affect influence over a connection's affiliate status? | Logistic regression on affiliate odds by language |
| **Sponsorship:** does affiliate status expand a streamer's network? | Regression of node degree on affiliate status, controlling for views and account lifetime |
| **Intercommunity relations:** do language communities depend on bridges? | Ranked cross-language edges by edge betweenness and removed them in stages, tracking views and affiliation |

## Key Findings

- **Popularity:** degree centrality tracked view counts better than eigenvector centrality. The relationship was positive in the Russian and Chinese communities but negative in the more fragmented Spanish community.
- **Power:** controlling for views, lifetime, and maturity, Chinese-speaking users had 38.2% lower odds of being affiliates than Spanish-speaking users. Being connected to a Spanish-speaking affiliate raised a user's odds of affiliation more (62.2%) than being connected to a Chinese-speaking one (44.7%).
- **Sponsorship:** contrary to our hypothesis, affiliates in the French, Spanish, and Russian communities had fewer mutual followers than non-affiliates, and there was no significant effect in the Chinese community.
- **Intercommunity ties:** removing the most important bridges lowered average views by 20% to 40% (about 27% on average), so cross-language connections matter more than we expected.

Together, these results suggest language is a structural factor in how visibility and influence are distributed on the platform.

## Limitations

We studied only 4 of about 20 language communities and excluded English. Mutual-follower ties do not capture how strong a relationship is, affiliate status is binary, and the data is a single snapshot, so we cannot make causal claims.

## Repository Contents

- [`twitch_report_compiled_preview.pdf`](./twitch_report_compiled_preview.pdf): final report
- [`QSS_PPT.pdf`](./QSS_PPT.pdf): presentation slides
- [`final_proj_data.ipynb`](./final_proj_data.ipynb): data cleaning, community construction, and exploratory analysis
- [`proj.ipynb`](./proj.ipynb): network metrics, centrality analysis, and the bridge-removal experiment

The notebooks are included as a record of the analysis. They are not set up to run end to end, since they depend on the SNAP dataset, which must be downloaded separately.

## My Contribution

- Prepared and pruned the dataset and built the language community graphs and the intercommunity graph
- Ran the structural analysis of each community, including density, degree distributions, and hierarchical clustering
- Carried out the popularity analysis and the bridge-removal experiment

## Team

- Annika Amrhein
- Precious Esielem
- Angelic McPherson ([@Angelic-Work](https://github.com/Angelic-Work))
- Malay Mehta
