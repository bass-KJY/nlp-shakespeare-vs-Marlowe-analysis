# Shakespeare and Christopher Marlowe: A Comparative Analysis via Text Mining

## Research Background
William Shakespeare and Christopher Marlowe were prominent playwrights of the English Renaissance. Despite Shakespeare's later debut, notable similarities between the two authors’ works have led scholars to suggest that Shakespeare may have been influenced by Marlowe.

## Research Objectives
- Analyze Shakespeare's plays by **genre** to explore narrative structures and thematic features using:
  - **Sentiment Analysis**
  - **Keyword Extraction (Topic Modeling)**
- Compare selected **thematically similar play pairs** from Shakespeare and Marlowe to identify:
  - Emotional trajectory similarities
  - Sentence-level similarity

### Comparison Pairs:
| Christopher Marlowe                  | William Shakespeare          |
|-------------------------------------|------------------------------|
| *The Jew of Malta*                  | *The Merchant of Venice*     |
| *Tamburlaine the Great*             | *Macbeth*                    |
| *Doctor Faustus*                    | *Richard III*                |

## Dataset Overview
### 1. Shakespeare Corpus (`.csv`)
- Fields: `play_name`, `genre`, `character`, `act`, `scene`, `sentence`, `text`, `sex`
- Source: Preprocessed and cleaned, no missing values.

### 2. Marlowe Corpus (`.html` → `.csv`)
- Converted and preprocessed to match Shakespeare data format (excluding `genre`)
- Missing `act` and `scene` values filled with `0`.

## Methods
- **Sentiment Analysis**: Using RoBERTa (positive/negative values, smoothed graph)
- **Keyword Analysis**: LDA Topic Modeling
- **Sentence Similarity**: `sentence-transformers/all-MiniLM-L6-v2` (threshold ≥ 0.7)

## Key Findings

### Shakespeare Genre Analysis
- **Emotion Flow**: Tragedies and comedies show similar arcs at the beginning and diverge in the end.
- **Main Keywords**:
  - Comedy: *Good*, *Love*
  - History: *King*, *Royal*
  - Tragedy: *Tears*, *Poor*

### Shakespeare vs. Marlowe Comparison
- **Sentiment Trends**: Both authors exhibit similar emotional shifts at key plot points.
- **Sentence Similarity**:
  - Overall match rate: ~4–5% (after filtering duplicates and stopwords)

## Conclusion
- Shakespeare's plays demonstrate **genre-specific emotional arcs** and **distinct thematic features**.
- While there are **some similarities** between Shakespeare and Marlowe’s plays, current evidence is insufficient to **confirm direct influence**.
- The study demonstrates the potential of **text mining in literary analysis**.

## Future Applications
- **Style Transfer**: Training models on specific literary styles to generate text.
- **Authorship Attribution**: Identifying anonymous or disputed texts via stylometric analysis.

