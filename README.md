# Full Stack Gen AI

Full Stack Gen AI V2 is a learning and experimentation workspace for modern NLP and GenAI techniques. It currently focuses on:

- Classic word embeddings (custom word2vec)
- State-of-the-Art (SOTA) transformer-based embeddings (sentence-transformers, OpenAI, Google Gemini)
- Core NLP preprocessing (tokenization, stopwords, stemming, lemmatization)
- Part-of-speech tagging and named entity recognition
- Playing with small text corpora to understand representation learning

---

## Project Structure

- [main.py](main.py) – minimal entry point (prints a greeting); reserved for future app logic.
- [april12](april12)
	- [custom_word2vec.ipynb](april12/custom_word2vec.ipynb) – trains and explores a custom `gensim` word2vec model on small story texts from `data/`.
	- [custom_word2vec_V2.ipynb](april12/custom_word2vec_V2.ipynb) – enhanced version training Word2Vec on AI-focused corpus with deeper semantic exploration.
	- [data](april12/data)
		- [story1.txt](april12/data/story1.txt) – sample text corpus 1.
		- [story2.txt](april12/data/story2.txt) – sample text corpus 2.
		- [ai.txt](april12/data/ai.txt) – AI-focused text corpus for V2 training.
- [april_11](april_11)
	- [word2vec.ipynb](april_11/word2vec.ipynb) – earlier word2vec experimentation (embeddings, similarity, analogies, etc.).
- [april18](april18)
	- [SOTA.ipynb](april18/SOTA.ipynb) – explores state-of-the-art embedding models via sentence-transformers (`all-MiniLM-L6-v2`), OpenAI SDK, and Google Gemini via LangChain.
- [NLP](NLP)
	- [tokenization](NLP/tokenization)
		- [tokenizations.ipynb](NLP/tokenization/tokenizations.ipynb) – basic tokenization techniques.
		- [stopwords.ipynb](NLP/tokenization/stopwords.ipynb) – stopword removal experiments.
		- [stemming_lemmatization.ipynb](NLP/tokenization/stemming_lemmatization.ipynb) – stemming vs. lemmatization.
		- [partsofspeech_tagging.ipynb](NLP/tokenization/partsofspeech_tagging.ipynb) – POS tagging with NLTK (tags for words, filtering stopwords).
		- [name_entity_recognition.ipynb](NLP/tokenization/name_entity_recognition.ipynb) – basic named entity recognition (NER) using NLTK’s `ne_chunk`.

Supporting files:

- [pyproject.toml](pyproject.toml) – project metadata and main dependency list (Python ≥ 3.11).
- [requirements.txt](requirements.txt) – pip-style dependency list, useful for quick environment setup.

---

## Key Dependencies

Core libraries used across notebooks and future scripts:

- `gensim` – training and using word2vec and other embeddings.
- `numpy`, `pandas`, `scipy` – numerical and data utilities.
- `scikit-learn` – ML utilities (e.g., vector operations, evaluation).
- `nltk` – tokenization, stopwords, stemming/lemmatization helpers.
- `sentence-transformers`, `huggingface` – modern transformer-based embeddings (for later experiments).
- `langchain`, `langchain-community`, `langchain-openai`, `langchain-google-genai` – building LLM/GenAI workflows.
- `ipykernel` – Jupyter kernel support for notebooks.

---

## Setup

1. Clone the repo and create a virtual environment (recommended):

	 ```bash
	 python -m venv .venv
	 source .venv/bin/activate  # macOS / Linux
	 # On Windows: .venv\\Scripts\\activate
	 ```

2. Install dependencies (choose one):

	 Using `pyproject.toml` with uv or pip:

	 ```bash
	 # with uv (recommended if installed)
	 uv sync

	 # or with pip
	 pip install -r requirements.txt
	 ```

3. Ensure you are using Python ≥ 3.11 (as specified in pyproject.toml).

---

## Running Things

- Run the simple entry script:

	```bash
	python main.py
	```

- Work with notebooks:

	1. Activate your virtual environment.
	2. Start Jupyter (or VS Code’s notebook interface):

		 ```bash
		 python -m ipykernel install --user --name full-stack-genai-v2
		 ```

	3. Open and run notebooks such as:
		 - [april12/custom_word2vec.ipynb](april12/custom_word2vec.ipynb)
		 - [april_11/word2vec.ipynb](april_11/word2vec.ipynb)
		 - [NLP/tokenization/tokenizations.ipynb](NLP/tokenization/tokenizations.ipynb)

---

## Workflows

### 1. NLP Preprocessing Workflow

```mermaid
flowchart LR
		A[Raw text paragraph] --> B[Sentence tokenization]
		B --> C[Word tokenization]
		C --> D[Lowercasing & basic cleanup]
		D --> E[Stopword removal]
		E --> F[Stemming / Lemmatization]
		F --> G[POS tagging]
		G --> H[Named Entity Recognition]
```

- Implemented across:
	- [NLP/tokenization/tokenizations.ipynb](NLP/tokenization/tokenizations.ipynb)
	- [NLP/tokenization/stopwords.ipynb](NLP/tokenization/stopwords.ipynb)
	- [NLP/tokenization/stemming_lemmatization.ipynb](NLP/tokenization/stemming_lemmatization.ipynb)
	- [NLP/tokenization/partsofspeech_tagging.ipynb](NLP/tokenization/partsofspeech_tagging.ipynb)
	- [NLP/tokenization/name_entity_recognition.ipynb](NLP/tokenization/name_entity_recognition.ipynb)

### 2. Word2Vec Experiment Workflow

```mermaid
flowchart LR
		A[Load raw stories from data/] --> B[Clean & tokenize text]
		B --> C[Train custom gensim Word2Vec model]
		C --> D[Explore embeddings: similarity, analogies]
		D --> E[Inspect "odd one out" and vector relationships]
```

- Implemented in:
	- [april12/custom_word2vec.ipynb](april12/custom_word2vec.ipynb)
	- [april12/custom_word2vec_V2.ipynb](april12/custom_word2vec_V2.ipynb) (enhanced version)
	- [april_11/word2vec.ipynb](april_11/word2vec.ipynb)

### 3. SOTA Embedding Models Workflow

```mermaid
flowchart LR
		A[Input text / corpus] --> B{Choose embedding source}
		B -->|Open source| C[sentence-transformers<br/>all-MiniLM-L6-v2]
		B -->|Proprietary| D[OpenAI API<br/>text-embedding-3]
		B -->|Generative| E[Google Gemini<br/>via LangChain]
		C --> F[Generate dense vectors<br/>384-dim embeddings]
		D --> F
		E --> F
		F --> G[Semantic similarity,<br/>clustering, retrieval]
		G --> H[Downstream tasks:<br/>RAG, classification, etc.]
```

- Implemented in:
	- [april18/SOTA.ipynb](april18/SOTA.ipynb)

### 4. Complete Learning Journey

```mermaid
flowchart TD
		subgraph nlp["NLP Foundations"]
			T1["Tokenization<br/>(tokenizations.ipynb)"]
			T2["Stopwords<br/>(stopwords.ipynb)"]
			T3["Stemming/Lemmatization<br/>(stemming_lemmatization.ipynb)"]
			T4["POS Tagging<br/>(partsofspeech_tagging.ipynb)"]
			T5["NER<br/>(name_entity_recognition.ipynb)"]
			T1 --> T2 --> T3 --> T4 --> T5
		end
		subgraph embed["Embedding Models"]
			E1["Word2Vec Basics<br/>(word2vec.ipynb)"]
			E2["Custom Word2Vec<br/>(custom_word2vec.ipynb)"]
			E3["Word2Vec V2<br/>(custom_word2vec_V2.ipynb)"]
			E1 --> E2 --> E3
		end
		subgraph sota["State-of-the-Art"]
			S1["SOTA Models<br/>(SOTA.ipynb)<br/>sentence-transformers<br/>OpenAI + Gemini"]
		end
		T5 -->|Preprocessing| E1
		E3 -->|Classic approach| S1
		S1 -->|Production-ready| F["Downstream applications:<br/>semantic search, RAG,<br/>clustering, classification"]
```

- **Foundation tier**: Master core NLP preprocessing with NLTK.
- **Embedding tier**: Progress from classic Word2Vec to enhanced custom implementations.
- **SOTA tier**: Integrate production-ready transformer embeddings and API-based models.

### 5. Text to Vector: From Tokens to Dense Embeddings

```mermaid
flowchart LR
	A["Raw Text"] -->|Preprocess| B["Clean Tokens"]
	B -->|Shallow embeddings| C["Word2Vec<br/>Skip-gram/CBOW"]
	B -->|Deep embeddings| D["Transformers<br/>Attention layers"]
	C --> E["Sparse context<br/>~300 dims"]
	D --> F["Rich semantics<br/>384-1536 dims"]
	E --> G["Vector Space"]
	F --> G
	G -->|Query| H["Similarity Search<br/>Clustering<br/>Retrieval"]
```

- Illustrates the progression from raw text through preprocessing to embeddings (classical vs. modern).
- Shows why transformer embeddings capture richer semantic information.

### 6. Tech Stack Integration

```mermaid
flowchart LR
	subgraph data["Data Layer"]
		D1["txt files<br/>data/"]
	end
	subgraph process["Processing Layer"]
		P1["NLTK<br/>tokenization,<br/>POS, NER"]
		P2["scikit-learn<br/>vectors,<br/>metrics"]
	end
	subgraph embed["Embedding Layer"]
		E1["gensim<br/>Word2Vec"]
		E2["sentence-transformers<br/>all-MiniLM"]
		E3["OpenAI<br/>API"]
		E4["Google Gemini<br/>API"]
	end
	subgraph app["Application Layer"]
		A1["Similarity<br/>search"]
		A2["Semantic<br/>clustering"]
		A3["RAG<br/>systems"]
		A4["Classification"]
	end
	D1 --> P1
	P1 --> P2
	P2 --> E1
	P2 --> E2
	E2 --> E3
	E3 --> E4
	E1 --> A1
	E2 --> A1
	E3 --> A3
	E4 --> A3
	E1 --> A2
	E2 --> A2
	E2 --> A4
```

- Shows how different libraries and APIs integrate across your tech stack.
- Demonstrates data flow from collection through processing to application.

### 7. Notebook Overview (Concept Map)

| Notebook | Focus | Key Concepts |
|---------|-------|--------------|
| [NLP/tokenization/tokenizations.ipynb](NLP/tokenization/tokenizations.ipynb) | Tokenization | Sentence/word tokenization, NLTK basics |
| [NLP/tokenization/stopwords.ipynb](NLP/tokenization/stopwords.ipynb) | Stopwords | Stopword lists, filtering tokens |
| [NLP/tokenization/stemming_lemmatization.ipynb](NLP/tokenization/stemming_lemmatization.ipynb) | Normalization | Stemming vs. lemmatization, trade-offs |
| [NLP/tokenization/partsofspeech_tagging.ipynb](NLP/tokenization/partsofspeech_tagging.ipynb) | POS tagging | Tags for words, filtering content words |
| [NLP/tokenization/name_entity_recognition.ipynb](NLP/tokenization/name_entity_recognition.ipynb) | NER | Named entities, chunking with ne_chunk |
| [april12/custom_word2vec.ipynb](april12/custom_word2vec.ipynb) | Custom embeddings | Training Word2Vec, exploring similarity |
| [april12/custom_word2vec_V2.ipynb](april12/custom_word2vec_V2.ipynb) | Enhanced Word2Vec | Skip-gram, 300-dim vectors, semantic relationships |
| [april_11/word2vec.ipynb](april_11/word2vec.ipynb) | Embedding sandbox | Classic word2vec experiments |
| [april18/SOTA.ipynb](april18/SOTA.ipynb) | SOTA embeddings | Transformer-based embeddings, HuggingFace, LangChain integration |

---

## Notes

- Some older `gensim` APIs (e.g., `doesnt_match`) have changed or been removed in gensim 4; notebooks may include small helper functions to replicate legacy behavior.
- SOTA notebooks leverage `sentence-transformers` for efficient transformer embeddings; also demonstrate API integration with OpenAI and Google Gemini via LangChain.
- Type hints and Pylance integration: Use `numpy-stubs` for better IDE autocomplete on NumPy arrays (e.g., `.shape`, `.dtype`).
- This repository is intended for experimentation and learning; breaking changes to notebooks are possible as you iterate.