# CodeSemanticSearch
A code search engine that takes in natural language queries and outputs Python functions corresponding to the queries. Uses data from the CodeSearchNet challenge.

The search engine uses ElasticSearch to store and search through the Python functions, its code, documentation, and other related attributes. Uses LambdaRank to re-rank the initial ElasticSearch results.

*If using LTR and want to use pre-made embeddings, download here: https://drive.google.com/drive/folders/10DAVFMzN92u_Y9yQSr6EOKbubgRzHe1K?usp=sharing 

To run the search engine:
1) Open the command prompt
2) Install and open Docker Desktop 
3) Run the following commands:
   -  `python -m venv code_search_venv` : creates the virtual Python environment
   -  `code_search_venv\Scripts\activate` : opens the created virtual environment
   -  `pip install -r requirements.txt` : installs necessary dependencies
   -  `docker run --rm -p 9200:9200 -p 9300:9300 -e "xpack.security.enabled=false" -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:8.7.0 ` : runs an ElasticSearch container through Docker
4) Open Jupyter Notebook (make sure you are using the created virtual Python environment)
5) Run the code in the `elastic_search_engine.ipynb` file

To evaluate the search engine (after running the code in the `elastic_search_engine.ipynb` file):
1) `cd..`: go back a level in the directory
2) `evaluation\relevanceeval.py evaluation\annotation_store.csv predictions\ltr_es_model_predictions.csv`: runs the evaluation script that outputs the NDCG score of the search engine on the annotated queries

## Additional Notes
- Within the `elastic_search.ipynb`, there are a few areas the user can modify code (view the commented out sections)
   - use a smaller subset of the data
   - create their own embeddings
- The `code_search_engine.ipynb` is an older version of our attempt at the CodeSearchNet challenge that does not implement Elasticsearch
