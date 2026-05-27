# The Dataset

### Philippine Fake News Corpus
This competition uses a comprehensive collection of 22,458 raw news articles from various Philippine media landscapes.
* **Credible Sources:** 14,802 articles from mainstream broadsheets including the Inquirer, Manila Bulletin, and Manila Times.
* **Not-Credible Sources:** 7,656 articles from outlets cited as unreliable or satire sources by established monitoring groups.

### Source-Level Mapping
Ground-truth labels for the leaderboard are derived from the source website and its historical classification:

| Source(s) | Manipulation Type | Description |
| :--- | :--- | :--- |
| Adobo Chronicles | Satire-as-fact | Self-described satire mixing facts with fabricated quotes. |
| Get Real Philippines, GR Pundit | Opinion-as-fact | Editorial opinion presented as straight reporting. |
| Thinking Pinoy, Duterte Today | Politically-motivated fabrication | Documented cases of fabricated quotes and events. |
| VerifiedPH, Pinoy Trending News | Misleading-headline | Sensationalized or false headlines attached to real content. |
| Pinoy News Blogger, etc. | Fabricated | Content with no basis in verifiable events or reporting. |
| Inquirer, Bulletin, Times | Authentic | Mainstream credible broadsheets. |

### Dataset Details
* **Timeline:** Articles range from January 1, 2016, to October 31, 2018.
* **Languages:** Includes Filipino, Taglish, and regional languages.
* **Format:** Every record is real, sourced content with no synthetic augmentation.
* **Dataset Access:** https://huggingface.co/datasets/SEACrowd/ph_fake_news_corpus
* **GitHub (Original):** https://github.com/aaroncarlfernandez/Philippine-Fake-News-Corpus
* **Original Work:** Fernandez, A.C. (2018). Computing the Linguistic-Based Cues of Fake News in the Philippines Towards its Detection. Master's Thesis. Mapua University.

### Files
* **test.csv:** The inference set containing the record index and raw article content.
* **sample_submission.csv:** A template showing the required 134,748-row submission format.