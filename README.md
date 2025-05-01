# 🎬 Reel Rascal

A cinephile's best friend: an AI companion that makes life more cinematic, one dialogue at a time.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Movie Count](https://img.shields.io/badge/movies-10K+-blue.svg)](https://github.com/your-username/cinematic-rascal)

## 📽️ Overview

Reel Rascal is not just another movie chatbot. It's an AI companion designed for movie lovers who sometimes need a friend to quote films with, discover hidden cinematic gems, or just chat about the latest releases. Supporting English, Hindi, and Kannada languages, this bot transforms ordinary conversations into cinematic experiences.

## 🎯 Core Functionality

- **Dialogue Mode**: Converse using iconic movie dialogues and character personalities
- **Recommendation Mode**: Get personalized film suggestions based on preferences and viewing history
- **Trivia Mode**: Explore fascinating behind-the-scenes facts about your favorite films
- **Review Mode**: Generate insightful film critiques in various styles

## 🛠️ Technical Architecture

### Data Sources & Preprocessing

| Source | Data Type | Processing |
|--------|-----------|------------|
| IMDb | Cast info, ratings, technical details | JSON parsing, entity extraction |
| Rotten Tomatoes | Critical reviews, audience scores | Sentiment analysis, opinion extraction |
| Wikipedia | Plot summaries, production info | Text chunking, entity recognition |
| Movie Scripts | Dialogues, character relationships | Scene segmentation, speaker identification |

### RAG Implementation

```
                                +-------------------+
                                |                   |
                                |  User Interface   |
                                |                   |
                                +--------+----------+
                                         |
                                         v
+------------------+           +---------+---------+           +------------------+
|                  |           |                   |           |                  |
|  Vector Database |<--------->|  Retrieval Engine |<--------->|  Language Model  |
|    (Chroma DB)   |           |                   |           |  (LLaMA 3 70B)   |
|                  |           +---------+---------+           |                  |
+------------------+                     |                     +------------------+
                                         |
                              +----------v-----------+
                              |                      |
                              |  Embedding Model     |
                              | (sentence-transformers)|
                              |                      |
                              +----------------------+
```

### Components

#### Vector Database
- **Chroma DB**: Chosen for its performance-to-simplicity ratio and Python integration
- Document schema includes metadata for film IDs, languages, genres, and release dates
- Hybrid search combining semantic and keyword-based retrieval

#### Embedding Generation
- **Model**: BAAI/bge-large-en-v1.5 (for English content)
- **Multilingual**: XLM-RoBERTa-large for Hindi and Kannada content
- **Chunking Strategy**: 
  - Plot summaries: 500-token chunks with 50-token overlap
  - Dialogues: Scene-level segmentation with character context
  - Reviews: Paragraph-level with sentiment preservation

#### Language Model
- **Base Model**: LLaMA 3 70B or Claude 3.5 Sonnet (depending on deployment constraints)
- **Instruction Dataset**: Custom curated examples of cinematic dialogue and film analysis
- **Prompt Engineering**: Specialized templates for each mode with explicit retrieval integration

#### Retrieval Optimization
- Dynamic retrieval depth based on query complexity
- Re-ranking with cross-encoder model for improved relevance
- Contextual retrieval incorporating user session history

## 🔧 Development Roadmap

- [x] Initial data collection and preprocessing
- [x] Prototype RAG implementation
- [ ] Character personality modeling
- [ ] Multi-language support refinement
- [ ] Deployment architecture finalization
- [ ] Community contribution framework
- [ ] Web interface development



## 🤝 Contribution Guidelines

This project requires significant data curation efforts. If you're interested in contributing:

1. **Data Collection**: Help with scraping and cleaning movie data
2. **Dialogue Curation**: Contribute to our database of iconic movie dialogues
3. **Multilingual Support**: Assist with Hindi and Kannada language resources
4. **Model Evaluation**: Test retrieval quality and response accuracy

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed instructions.

## ⚠️ Challenges & Limitations

- **Web Scraping Obstacles**: Captchas, IP blocks, and changing website structures make data collection challenging
- **Content Licensing**: Using copyrighted dialogue requires careful fair-use consideration
- **Multilingual Coverage**: Kannada and regional Indian cinema have less structured data available online
- **Computational Requirements**: Optimal performance requires significant computational resources

## 📜 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) for details.

## 🙏 Acknowledgements

- IMDb, Rotten Tomatoes, and Wikipedia for making film data accessible
- The open-source ML community for model development and tools
- All contributors who help curate our growing database of cinematic knowledge

---

*I need to touch grass*
