# Blockchain-based Research Paper Analysis

This project analyzes a dataset of 348 research papers to identify key topics using **Latent Dirichlet Allocation (LDA)**. The goal is to provide a clear and interactive visualization of the main themes discussed in the papers, particularly those related to **blockchain technology**.

-----

## 🚀 Key Features

  * **Data Preparation:** The project preprocesses raw text data from research papers, combining titles, abstracts, and keywords into a single corpus.
  * **Text Cleaning:** It includes steps for cleaning the text, such as removing stopwords, tokenization, and lemmatization, to prepare it for topic modeling.
  * **Topic Modeling with LDA:** The project uses the **`gensim`** library to train an LDA model, which identifies 20 distinct topics from the dataset.
  * **Interactive Visualization:** It uses **`pyLDAvis`** to create an interactive web-based visualization of the topics, allowing for a deeper understanding of the relationships between topics and keywords.
  * **Word Cloud Generation:** A **word cloud** is generated to visually represent the most frequent words in the dataset before preprocessing.

-----

## 🛠️ Installation

To run this project, you'll need to install the following Python libraries. You can install them using `pip`:

```bash
pip install numpy gensim pyLDAvis wordcloud pandas scikit-learn
```

-----

## 💻 Usage

1.  **Clone the Repository:**

    ```bash
    git clone https://github.com/your-username/your-repository-name.git
    cd your-repository-name
    ```

2.  **Prepare your data:** Ensure your research paper data is in an Excel file named `Book1.xlsx` in the project's root directory. The file should contain columns for `Title`, `Abstract`, `Author Keywords`, and `Index Keywords`.

3.  **Run the analysis:** The core logic is implemented in a Python script (or a Jupyter Notebook). Execute the script to perform the topic modeling and generate the visualizations.

    The code performs the following steps:

      * Loads data from `Book1.xlsx`.
      * Combines text from relevant columns into a new `text` column.
      * Generates a word cloud of the raw text.
      * Cleans and preprocesses the text data.
      * Creates a dictionary and corpus for LDA.
      * Trains an LDA model with 20 topics.
      * Computes and displays the **perplexity** and **coherence score** of the model to evaluate its performance.
      * Generates and displays the interactive **`pyLDAvis`** visualization.

-----

## 📊 Results

The project produces two key visualizations:

### 1\. Word Cloud

A word cloud provides a quick overview of the most frequently used words in the dataset.

### 2\. Interactive Topic Visualization

The **`pyLDAvis`** output provides an interactive way to explore the topics. It displays:

  * A scatter plot where each circle represents a topic. The size of the circle corresponds to the prevalence of the topic.
  * The distance between circles indicates the similarity between topics.
  * A list of the most relevant keywords for a selected topic, allowing you to interpret what each topic is about.

Here's an example of the topics identified by the LDA model:

  * **Topic 0:** `blockchain`, `design`, `business`, `smart`, `science`, `construction`
  * **Topic 1:** `blockchain`, `design`, `insurance`, `healthcare`, `financial`, `technology`
  * **Topic 9:** `blockchain`, `chain`, `supply`, `smart`, `design`, `approach`, `traceability`
  * **Topic 14:** `information`, `healthcare`, `blockchain`, `design`, `patient`, `sharing`
