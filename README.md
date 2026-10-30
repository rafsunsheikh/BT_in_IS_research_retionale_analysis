<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![License][license-shield]][license-url]

<br />
<div align="center">
  <h1 align="center">Blockchain Research Topic Analysis</h1>
  <p align="center">
    LDA topic modelling of 348 blockchain research papers, built from their titles, abstracts and keywords.
    <br /><br />
    <a href="#getting-started"><strong>Get started »</strong></a>
    <br /><br />
    <a href="#results">Results</a>
    &middot;
    <a href="#methodology">Methodology</a>
    &middot;
    <a href="https://github.com/rafsunsheikh/BT_in_IS_research_retionale_analysis/issues">Report Bug</a>
  </p>
</div>

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#key-features">Key Features</a></li>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li><a href="#notebooks">Notebooks</a></li>
    <li><a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#results">Results</a></li>
    <li><a href="#methodology">Methodology</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

## About The Project

This project uses **Latent Dirichlet Allocation (LDA)** to find the main themes in a set of 348 research papers about **blockchain technology**. Each paper is represented by its title, abstract, author keywords and index keywords. The notebooks clean this text, train LDA topic models with Gensim, compare models with different numbers of topics using coherence scores, and show the topics with interactive and static charts.

The result is a clear picture of which application areas the papers cover. For example, the 20 topic model separates topics on supply chains and traceability, healthcare information sharing, real estate transactions, and energy and emissions.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Key Features

* **Data preparation.** Combines the `Title`, `Abstract`, `Author Keywords` and `Index Keywords` of each paper into one text per paper.
* **Text cleaning.** Removes English stopwords plus a custom list of common academic words, and tokenizes the text with Gensim.
* **Topic modelling with LDA.** Trains Gensim LDA models with 20 and with 50 topics.
* **Choosing the number of topics.** Trains models with 2 to 49 topics and plots their `c_v` coherence scores.
* **Interactive visualisation.** Uses `pyLDAvis` to show how topics relate to each other and which words define each topic.
* **Word clouds and charts.** Draws a word cloud of the raw text, word clouds of the top words per topic, document length histograms and keyword weight charts.
* **PDF to text helper.** A separate notebook converts a folder of PDF papers into a CSV of plain text.

### Built With

* [![Python][python-shield]][python-url]
* [![Jupyter][jupyter-shield]][jupyter-url]
* [![Google Colab][colab-shield]][colab-url]
* [Gensim][gensim-url] for the dictionary, corpus, LDA models, perplexity and coherence
* [NLTK][nltk-url] for stopwords
* [pyLDAvis][pyldavis-url] for the interactive topic map
* [pandas][pandas-url], [Matplotlib][matplotlib-url], [seaborn][seaborn-url] and [WordCloud][wordcloud-url] for data handling and charts
* [pdfminer.six][pdfminer-url] for turning PDFs into text

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Notebooks

| Notebook | What it does | Open |
|----------|--------------|------|
| [`DSR_in_BT_SLR_LDA.ipynb`](DSR_in_BT_SLR_LDA.ipynb) | Main analysis with a 20 topic LDA model | [![Open In Colab][colab-badge]][colab-20] |
| [`DSR_in_BT_SLR_LDA_50_topics.ipynb`](DSR_in_BT_SLR_LDA_50_topics.ipynb) | The same analysis with a 50 topic LDA model and a tuned topic count search | [![Open In Colab][colab-badge]][colab-50] |
| [`PDF_to_TXT_file.ipynb`](PDF_to_TXT_file.ipynb) | Converts a folder of PDF files to text and saves it as a CSV | [![Open In Colab][colab-badge]][colab-pdf] |

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Getting Started

The notebooks were written for Google Colab, but they also run in a local Jupyter setup.

> **Note:** The paper data (`Book1.xlsx`) is not included in this repository. You need to supply your own file in the format described below.

### Prerequisites

* Python 3
* Jupyter, or a Google account to use Google Colab

### Installation

1. Clone the repository
   ```sh
   git clone https://github.com/rafsunsheikh/BT_in_IS_research_retionale_analysis.git
   cd BT_in_IS_research_retionale_analysis
   ```
2. Install the Python packages the notebooks import (`openpyxl` lets pandas read the Excel file)
   ```sh
   pip install numpy pandas gensim pyLDAvis wordcloud nltk matplotlib seaborn spacy openpyxl
   ```
3. For the PDF to text notebook, also install pdfminer.six (the notebook mentions version `20200124`)
   ```sh
   pip install "pdfminer.six==20200124"
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Usage

1. **Prepare your data.** Create an Excel file named `Book1.xlsx` with one row per paper and the columns `Title`, `Abstract`, `Author Keywords` and `Index Keywords`. The notebooks read it from `/content/Book1.xlsx`, which is the default Colab upload folder. Change `file_path` if you run them somewhere else.
2. **Run the analysis.** Open `DSR_in_BT_SLR_LDA.ipynb` (20 topics) or `DSR_in_BT_SLR_LDA_50_topics.ipynb` (50 topics) and run all cells. The notebook will:
   * load the data from `Book1.xlsx`
   * combine the four text columns into a new `text` column
   * draw a word cloud of the raw text
   * clean and tokenize the text
   * build a dictionary and corpus for LDA
   * train the LDA model
   * print the model's **perplexity** and **coherence score**
   * show the interactive **pyLDAvis** chart
   * find the dominant topic of each paper and save the topic table to `LDA_topic_modeling.csv`
3. **Optional: convert PDFs to text.** In `PDF_to_TXT_file.ipynb`, set `folder_path` to a folder of PDF files and run all cells. It writes the extracted text to a CSV file and lists any PDFs it could not read.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Results

The scores below come from the saved notebook outputs.

| Model | Training settings | Perplexity (log) | Coherence (`c_v`) |
|-------|-------------------|-----------------:|------------------:|
| 20 topics | `passes=50`, `iterations=100` | -7.632 | 0.285 |
| 50 topics | `passes=100`, `iterations=100` | -7.633 | 0.313 |

### Word Cloud

A word cloud of the combined raw text gives a quick view of the most frequent words before cleaning.

### Interactive Topic Visualisation

The **pyLDAvis** output lets you explore the topics. It shows:

* a scatter plot where each circle is a topic, and the size of the circle shows how common the topic is
* the distance between circles, which shows how similar the topics are
* the most relevant keywords for the selected topic, which helps you work out what each topic is about

### Example Topics

Some of the topics found by the 20 topic model (top words):

* **Topic 0:** `blockchain`, `design`, `business`, `smart`, `science`, `construction`
* **Topic 1:** `blockchain`, `design`, `insurance`, `healthcare`, `financial`, `technology`
* **Topic 7:** `blockchain`, `emissions`, `energy`, `sustainable`, `greenhouse`, `gas`
* **Topic 8:** `real`, `estate`, `design`, `blockchain`, `transaction`, `science`
* **Topic 9:** `blockchain`, `chain`, `supply`, `smart`, `design`, `approach`, `traceability`
* **Topic 14:** `information`, `healthcare`, `blockchain`, `design`, `patient`, `sharing`

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Methodology

### 1. Data preparation

Each row of `Book1.xlsx` is one paper. The notebook keeps the `Title`, `Abstract`, `Author Keywords` and `Index Keywords` columns and joins them into one `text` field. This gives 348 documents.

### 2. Text cleaning

* English stopwords from NLTK are removed, together with a custom list of common words such as `research`, `journal`, `doi`, `using` and `based`.
* The text is split into lowercase tokens with Gensim's `simple_preprocess` (with `deacc=True`, which also removes punctuation and accents).
* The notebooks also define a lemmatize and stem helper (WordNet lemmatizer plus Porter stemmer) and show it on one example paper. The LDA models are trained on the cleaned tokens from the step above.

### 3. Dictionary and corpus

A Gensim `Dictionary` maps each word to an id, and each paper becomes a bag of words (a list of word id and count pairs).

### 4. Training the LDA models

Both notebooks use `gensim.models.ldamodel.LdaModel` with `random_state=100` and `chunksize=1000`:

```python
# DSR_in_BT_SLR_LDA.ipynb
lda_model = LDA(corpus=doc_term_matrix, id2word=dictionary, num_topics=20, random_state=100,
                chunksize=1000, passes=50, iterations=100)

# DSR_in_BT_SLR_LDA_50_topics.ipynb
lda_model = LDA(corpus=doc_term_matrix, id2word=dictionary, num_topics=50, random_state=100,
                chunksize=1000, passes=100, iterations=100)
```

### 5. Evaluation and choosing the number of topics

* Each model's log perplexity and `c_v` coherence are printed (see [Results](#results)).
* A `compute_coherence_values` function trains one model for every topic count from 2 to 49 and plots the coherence scores. The first notebook uses Gensim's default training settings for this search. The 50 topic notebook uses `random_state=100`, `passes=30` and `iterations=100`.
* A model from this search is then picked and shown with pyLDAvis: the 10 topic model in the first notebook and the 22 topic model in the 50 topic notebook.

### 6. Topic analysis outputs

* The dominant topic, its share and its keywords for every paper
* The most representative paper for each topic
* The number and share of papers per topic, saved to `LDA_topic_modeling.csv`
* Histograms of document word counts, overall and per topic
* Word clouds of the top 10 words for the first four topics
* Bar charts that compare word counts with keyword weights for the first four topics

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for details.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contact

MD Rafsun Sheikh: [@rafsunsheikh](https://github.com/rafsunsheikh)

Project link: [https://github.com/rafsunsheikh/BT_in_IS_research_retionale_analysis](https://github.com/rafsunsheikh/BT_in_IS_research_retionale_analysis)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/rafsunsheikh/BT_in_IS_research_retionale_analysis.svg?style=for-the-badge
[contributors-url]: https://github.com/rafsunsheikh/BT_in_IS_research_retionale_analysis/graphs/contributors
[stars-shield]: https://img.shields.io/github/stars/rafsunsheikh/BT_in_IS_research_retionale_analysis.svg?style=for-the-badge
[stars-url]: https://github.com/rafsunsheikh/BT_in_IS_research_retionale_analysis/stargazers
[issues-shield]: https://img.shields.io/github/issues/rafsunsheikh/BT_in_IS_research_retionale_analysis.svg?style=for-the-badge
[issues-url]: https://github.com/rafsunsheikh/BT_in_IS_research_retionale_analysis/issues
[license-shield]: https://img.shields.io/github/license/rafsunsheikh/BT_in_IS_research_retionale_analysis.svg?style=for-the-badge
[license-url]: https://github.com/rafsunsheikh/BT_in_IS_research_retionale_analysis/blob/main/LICENSE
[python-shield]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[python-url]: https://www.python.org/
[jupyter-shield]: https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white
[jupyter-url]: https://jupyter.org/
[colab-shield]: https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white
[colab-url]: https://colab.research.google.com/
[colab-badge]: https://colab.research.google.com/assets/colab-badge.svg
[colab-20]: https://colab.research.google.com/github/rafsunsheikh/BT_in_IS_research_retionale_analysis/blob/main/DSR_in_BT_SLR_LDA.ipynb
[colab-50]: https://colab.research.google.com/github/rafsunsheikh/BT_in_IS_research_retionale_analysis/blob/main/DSR_in_BT_SLR_LDA_50_topics.ipynb
[colab-pdf]: https://colab.research.google.com/github/rafsunsheikh/BT_in_IS_research_retionale_analysis/blob/main/PDF_to_TXT_file.ipynb
[gensim-url]: https://radimrehurek.com/gensim/
[nltk-url]: https://www.nltk.org/
[pyldavis-url]: https://github.com/bmabey/pyLDAvis
[pandas-url]: https://pandas.pydata.org/
[matplotlib-url]: https://matplotlib.org/
[seaborn-url]: https://seaborn.pydata.org/
[wordcloud-url]: https://github.com/amueller/word_cloud
[pdfminer-url]: https://github.com/pdfminer/pdfminer.six
