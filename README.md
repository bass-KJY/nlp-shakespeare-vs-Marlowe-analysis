# Shakespeare and Christopher Marlowe: A Comparative Text Mining Analysis

## Research Background
This project combines literary analysis with AI-powered computational techniques to explore stylistic and thematic similarities between two major English Renaissance playwrights: **William Shakespeare** and **Christopher Marlowe**.

While Shakespeare debuted after Marlowe, many have noted parallels in their work. This study aims to move beyond speculation and apply **quantitative analysis**—including **sentiment trends**, **topic modeling**, and **sentence similarity**—to assess how similar their texts actually are.

---

## Objectives
- **Intra-author Analysis**: Examine Shakespeare's plays by genre to identify **emotional narrative arcs** and **thematic markers**.
- **Inter-author Comparison**: Analyze thematically similar **play pairs** between Shakespeare and Marlowe using:
  - Sentiment flow alignment
  - Sentence embedding similarity
  - Topic distribution comparison

### Play Pairings for Comparison:

| Christopher Marlowe                  | William Shakespeare          |
|-------------------------------------|------------------------------|
| *The Jew of Malta*                  | *The Merchant of Venice*     |
| *Tamburlaine the Great*             | *Macbeth*                    |
| *Doctor Faustus*                    | *Richard III*                |

These were manually selected based on thematic and narrative similarities.

---

## Dataset Overview

### 1. Shakespeare Corpus (CSV)
- **Source**: [Kaggle dataset](https://www.kaggle.com/datasets/kingburrito666/shakespeare-plays)  
- **Fields**: `play_name`, `genre`, `character`, `act`, `scene`, `sentence`, `text`, `sex`
- **Note**: Fully structured with no missing values.

### 2. Marlowe Corpus (HTML → CSV)
- **Source**: Original HTML versions of Marlowe’s works from Project Gutenberg
- **Preprocessing**:
  - Removed stage directions and irrelevant text
  - Split by character and dialogue
  - Converted to CSV with structure matching Shakespeare's dataset
  - Missing `act` and `scene` info filled with `0`

---

## Models & Tools

| Task                  | Model / Tool                                                   | Description |
|-----------------------|----------------------------------------------------------------|-------------|
| **Sentiment Analysis** | `RoBERTa` (via HuggingFace)                                     | Captures nuanced emotions based on contextual understanding |
| **Topic Modeling**     | `LDA` (Latent Dirichlet Allocation via Scikit-learn)            | Extracts dominant themes/keywords per genre |
| **Sentence Similarity**| `sentence-transformers/all-MiniLM-L6-v2`                        | Embeds sentences for semantic similarity comparison |

---

## Methodology Overview

### 1. **Sentiment Analysis**
- Objective: Identify how emotions evolve over time in a play.
- Process:
  - Applied RoBERTa to each line of dialogue
  - Normalized sentiment over play length
  - Smoothed scores to reveal narrative trajectories
- Visualization: Line graphs showing shifts in sentiment over acts

#### A. Sentiment Analysis by Gerne of Shaspeaere Plays
- ![Each graph(Comedy, History, Tragedy) shows distinctions. Especially, Comedy's sentimental graph for the last part is rising, which means it is positive, but the tragedy is descending. (image/sentiment_change_gerne.png)

### 2. **Topic Modeling (Keyword Analysis)**
- Objective: Reveal dominant themes in each genre
- Process:
  - Removed stopwords
  - Applied LDA to group terms into genre-related topics
- Output: Top keywords per genre

### 3. **Sentence Similarity**
- Objective: Quantify textual similarity between authors
- Process:
  - Embedded each sentence using MiniLM
  - Calculated cosine similarity between play pairs
  - Kept only scores ≥ 0.7

---

## Results Summary

### Shakespeare: Sentiment by Genre
- **General Trend**: Comedies and tragedies start similarly but diverge at the end (comedy → upward, tragedy → downward).
- **Positive lines** slightly outnumber negatives across all genres.

### Genre-Specific Keywords

| Genre    | Top Keywords                |
|----------|-----------------------------|
| Comedy   | *Good*, *Love*              |
| History  | *King*, *Royal*, *Noble*    |
| Tragedy  | *Tears*, *Poor*             |

---

### Shakespeare vs. Marlowe: Emotional Alignment
- All matched play pairs show:
  - High negative emotion dominance
  - Similar emotional spikes around the climax
  - Notably aligned patterns in *Tamburlaine* vs. *Macbeth*

### 🔗 Sentence Similarity (Cosine ≥ 0.7)

| Pair                                | Matches (Shakespeare / Marlowe) | Match Rate |
|-------------------------------------|----------------------------------|------------|
| *Jew of Malta* / *Merchant*         | 135 / 2364                       | ~5.7%      |
| *Tamburlaine* / *Macbeth*           | 244 / 4891                       | ~5.0%      |
| *Faustus* / *Richard III*           | 63 / 1424                        | ~4.4%      |

→ Many similarities involve general expressions or dramatic cues.

---

## Interpretation & Discussion

- **Within Shakespeare**:
  - Sentiment flow reflects genre conventions
  - Keywords support thematic clustering (e.g., "Love" for comedy, "Tears" for tragedy)

- **Shakespeare vs. Marlowe**:
  - Despite **some emotional alignment** and **limited sentence similarity**, evidence is insufficient to **confirm direct influence**
  - Low match rate may stem from:
    - Sample size
    - Limited comparison scope
    - Generic expressions inflating similarity scores

---

## Future Applications

- **Authorship Attribution**: Use stylistic/semantic profiles to identify unknown writers
- **Style Transfer**: Train generative models to write in the style of specific playwrights
- **Comparative Literary Analytics**: Expand to more authors and genres (e.g., Jonson, Kyd)

---

## Acknowledgements

-  Data Sources:  
  - Shakespeare: Kaggle Open Dataset  
  - Marlowe: HTML sources via public domain (converted manually)

-  Tools:  
  - HuggingFace Transformers  
  - Scikit-learn (LDA)  
  - SentenceTransformers  
  - Python / Pandas / Matplotlib

---

> _“This project demonstrates how computational analysis can enhance literary research—revealing patterns, validating hypotheses, and bridging the gap between data science and the humanities.”_

