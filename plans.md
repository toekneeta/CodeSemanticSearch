**Architecture**: What steps will search do?

The data we will be using for search is the ‘whole_func_string’ column of the CodeSearchNet dataset, which is preprocessed by tokenization, removal of stop words, and lemmatization, after which the tokens are joined together into a string and then encoded into a vector space. We hope to also implement bigrams into our preprocessing to hopefully improve accuracy. We also may experiment with using the ‘func_documentation_string’ column for our data, which contains additional text on what the function does.

The search function itself takes the query string and encodes it before computing similarities between all other embeddings in our data, returning the top 25 results that have at least a 0.7 cosine similarity.

**Algorithms**: What is the math inside the steps in the architecture?

Initially, we are calculating the cosine similarity between the query embedding and all of our document embeddings. However, we want to see how well using Annoy to get approximate nearest neighbors will improve our search time (and perhaps accuracy as well), seeing as running cosine similarity has been slow.

**Dataset**: Which portions of the dataset will you use?

So far, we are performing search on the Python data subset as a smaller size makes operations more manageable. We may test our search on other languages, but we are primarily concerned with improving our accuracy on the Python set.

**Evaluation**: How will you measure the results? Do you have benchmarks?

We will use the given evaluation methods from the CodeSearchNet Challenge, which computes the normalized discounted cumulative gain (NDCG) for 99 natural language queries over (1) the subset of data with human annotations and (2) the entire CodeSearchNet corpus. We can compare our results to the baseline models outlined in the CodeSearchNet paper as well as the current CodeSearch leaderboard to assess and compare our model’s performance.

**Improvements**: A list of future work / stretch goals that you might try if you have time.
- Bigrams in pre-processing
- ANNOY for search engine
- Fine-tuning layers
- Search on other languages
