# AI-Steganography: BERTopic-Based Research Analysis [![License: MIT][License-Badge]](LICENSE)

A comprehensive topic modeling analysis of AI steganography research literature using BERTopic, revealing research trends, geographic distribution, and thematic landscapes across 1,050+ academic papers.

## 🎯 Overview

This project applies advanced natural language processing and clustering techniques to analyze research papers in the steganography domain. It automatically discovers 10 key research topics, tracks their evolution from 2017-2025, maps geographic contributions, and identifies influential papers.

### Key Findings

- **10 Distinct Topics**: From steganalysis to quantum steganography
- **1,050+ Papers**: Analyzed across 50+ countries
- **China-Dominant**: 59% of contributions (dominant research hub)
- **Emerging Focus**: GAN-based and medical image steganography gaining momentum
- **Citation Analysis**: Top 7 papers per topic ranked by impact

## 🏗️ Project Structure

```flowchart
AI-Steganography/
├── bert.ipynb                          Main analysis notebook
├── data.csv                            Input dataset (1,050+ papers)
├── cached_embeddings.npy               Pre-computed BERT embeddings
├── final_bertopic_model/               Trained BERTopic model
├── Top_Docs_per_topic/                 CSV exports of influential papers per topic
├── topic_country_matrix.csv            Geographic contribution matrix
├── topic_word_network.html             Interactive topic network visualization
├── CLAUDE.md                           Technical documentation
└── README.md                           This file
```

## 🚀 Quick Start

### Installation

```bash
# Core dependencies
pip install bertopic openai python-dotenv numpy pandas scikit-learn

# Visualization and analysis tools
pip install plotly wordcloud datamapplot pyvis

# Optional: GPU acceleration (NVIDIA only)
pip install cuml
```

### Running the Analysis

1. **Prepare Data**

   ```bash
   # Place your data.csv in the project directory with columns:
   # Abstract, Year, Cited by, Title, Authors, DOI, Country
   ```

2. **Run Notebook**

   ```bash
   jupyter lab bert.ipynb
   ```

3. **Outputs Generated**
   - Topic assignments and keywords
   - 5 interactive visualizations
   - Top papers per topic (CSV)
   - Country contribution analysis
   - Temporal trend plots

## 📊 Discovered Topics

| Topic | Focus Area | Papers | Key Terms |
| --- | --- | --- | --- |
| **0** | Steganalysis & Detection | 255 | steganalysis, detection, adversarial, CNN |
| **1** | Image Steganography | 254 | steganography, image, embedding, security |
| **2** | Digital Watermarking | 122 | watermarking, robust, attacks, fingerprinting |
| **3** | Adversarial Methods | 115 | adversarial, GAN, generation, imperceptible |
| **4** | Medical Applications | 111 | medical, data, encryption, patient privacy |
| **5** | Reversible Data Hiding | 63 | RDH, prediction, lossless, histogram |
| **6** | Covert Communication | 64 | covert, communication, traffic, learning |
| **7** | Text Steganography | 53 | text, linguistic, NLP, semantic |
| **8** | Audio Steganography | 45 | audio, speech, quantum, acoustic |
| **9** | Video Steganography | 36 | video, frame, motion, temporal |

## 📈 Analysis Capabilities

### 1. Topic Modeling

- BERT embeddings (384-dim) → UMAP reduction (10-30-dim) → HDBSCAN clustering
- c-TF-IDF for interpretable keyword extraction
- Automatic hyperparameter optimization via grid search

### 2. Visualizations

- **Heatmap**: Topic similarity and correlation
- **Bar Chart**: Top words per topic with frequencies
- **Scatter Plot**: Document-topic space (2D UMAP projection)
- **Hierarchy**: Topic relationships and sub-topics
- **Word Clouds**: Visual term frequency per topic
- **Network Graph**: Interactive topic-keyword connections
- **Temporal Trends**: Publication rates over time

### 3. Impact Analysis

- **Citation Metrics**: Top 7 papers per topic ranked by citation count
- **Normalized TC**: Citations relative to field baseline
- **TC/Year**: Citations per year since publication
- **Influence Distribution**: Identifies seminal papers

### 4. Geographic Analysis

- **Top 10 Countries** per topic
- **Contribution Matrix**: Topics × Countries contribution heatmap
- **Research Hubs**: China (59%), India (14%), USA (4%)

### 5. Temporal Evolution

- **10-Bin Trend Analysis**: Publications per 1-year intervals
- **Growth Rates**: Topic emergence and decline patterns
- **Peak Years**: Maximum publication activity per topic

## 🔬 Methodology

### Pipeline Overview

```flowchart
Raw Abstracts
    ↓
BERT Embeddings (all-MiniLM-L6-v2)
    ↓
UMAP Dimensionality Reduction
    ↓
HDBSCAN Clustering
    ↓
c-TF-IDF Topic Terms
    ↓
Azure OpenAI Topic Naming (Optional)
    ↓
Analysis & Visualization
```

### Hyperparameter Optimization

Grid search across:

- UMAP neighbors: [10, 20, 30]
- UMAP components: [10, 15, 20, 25, 30]
- HDBSCAN cluster size: [25, 30, 35]
- HDBSCAN min samples: [3, 5]

**Selection Criteria**: 5-10 topics, <10% outliers, no dominant topic >20%

### GPU Support

Automatic detection and use of RAPIDS cuML (3-5x speedup on NVIDIA GPUs).

## 📝 How to Use

### For General Users

1. Open `bert.ipynb` in Jupyter
2. Run all cells in order
3. View generated visualizations inline
4. Export data from `Top_Docs_per_topic/` and `topic_country_matrix.csv`

### For Researchers

- **Extend Analysis**: Modify grid search parameters in cell 13
- **Change Embeddings**: Replace `all-MiniLM-L6-v2` with other sentence-transformer models
- **Custom Vectorizer**: Adjust stopwords or n-gram range in cell 8
- **Topic Refinement**: Use `reduce_outliers()`, `reduce_topics()` methods

### For Data Scientists

- **Reproducibility**: Embeddings cached; set random_state for consistency
- **Performance**: GPU mode activated automatically if RAPIDS installed
- **Integration**: BERTopic model saved as pickle; load with `BERTopic.load()`

## 🔐 Requirements

- **Python**: 3.6+
- **Core**: NumPy ≥ 1.20.0, Pandas ≥ 1.1.5, scikit-learn ≥ 0.22.2
- **NLP**: sentence-transformers ≥ 0.4.1
- **Clustering**: HDBSCAN ≥ 0.8.29, UMAP ≥ 0.5.0
- **Visualization**: Plotly ≥ 4.7.0
- **Data**: CSV file with abstract text, year, and metadata columns

## 🌐 Optional: Azure OpenAI Integration

Generate topic names using Azure OpenAI GPT models:

```python
from openai import OpenAI
from dotenv import load_dotenv

load_dotenv()
client = OpenAI(
    api_key=os.getenv("FOUNDRY_KEY"),
    base_url=os.getenv("FOUNDRY_URI")
)

# Uncomment cell 29 in notebook to enable
```

**Environment Variables Required**:

- `FOUNDRY_URI`: Azure OpenAI endpoint
- `FOUNDRY_KEY`: API key

## 📚 Key Insights & Findings

### Research Landscape

- **Dominant Theme**: Steganalysis/detection research (24% of papers)
- **Emerging Growth**: GAN-based adversarial steganography
- **Niche Development**: Text and audio steganography (mature communities, lower output)
- **Medical Emergence**: Health privacy focus growing (2-3% annually)

### Geographic Insights

- **China**: Clear research dominance (59%), covering all topics
- **India**: Secondary hub (14%), strong in adversarial methods
- **Developed Nations**: US, UK, Australia focus on advanced topics (GAN, medical)
- **Collaboration**: Limited cross-country papers; mostly isolated research

### Impact Distribution

- **Highly Cited**: Topic 0 and 1 papers average 20-30 citations
- **Growth Trajectory**: Newer topics (8, 9) show increasing citation velocity
- **Citation Decay**: Classic papers (2015-2017) remain high-impact despite age

## 🛠️ Troubleshooting

| Issue | Solution |
| --- | --- |
| `ModuleNotFoundError: No module named 'bertopic'` | Run `pip install bertopic` |
| `FileNotFoundError: data.csv not found` | Place CSV file in project root |
| `CUDA out of memory` | Disable GPU or reduce batch size |
| Visualization not rendering | Restart Jupyter kernel |
| Embeddings shape mismatch | Regenerate `cached_embeddings.npy` |

## 📖 Documentation

- **Detailed Technical Docs**: See [CLAUDE.md](CLAUDE.md)
- **BERTopic Official**: <https://maartengr.github.io/BERTopic/>
- **Paper**: <https://arxiv.org/abs/2203.05794>

## 🤝 Contributing

Contributions welcome! Areas for enhancement:

- New embedding models (multilingual-e5, e5-large)
- Advanced topic refinement (LDA, CTM)
- Additional visualization types
- Performance optimizations
- Documentation improvements

To contribute:

1. Fork the repository
2. Create a feature branch
3. Submit a pull request with clear description

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) file for details.

**Original BERTopic**: Developed and maintained by [Maarten Grootendorst](https://github.com/MaartenGr/)

**This Implementation**: Copyright (c) 2026 [Saksham Kumar](https://github.com/polymath_saksh) and respective owners.

## 🙏 Acknowledgments

- **BERTopic** team for the excellent topic modeling framework
- **HuggingFace** for transformers and sentence-transformers
- **RAPIDS** team for GPU-accelerated clustering
- Academic community for steganography research

---

**Last Updated**: May 2026  
**Dataset Version**: 1,050 papers (2017-2025)  
**Status**: Completed and documented; open for contributions and extensions

[License-Badge]: https://img.shields.io/badge/License-MIT-blue.svg
