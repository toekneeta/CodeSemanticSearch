# CodeSemanticSearch
A semantic search engine that takes in natural language queries and outputs Python functions corresponding to the queries. Uses data from the CodeSearchNet challenge.

The search engine uses ElasticSearch to store and search through the Python functions, its code, documentation, and other related attributes. Uses LambdaRank to re-rank the initial ElasticSearch results.

*If using LTR and want to use pre-made embeddings, download here: https://drive.google.com/drive/folders/10DAVFMzN92u_Y9yQSr6EOKbubgRzHe1K?usp=sharing 

To run the search engine:
1) Open Ubuntu (or any other Unix-based terminal)
2) Install Docker
3) Run the following commands on :
   - `python3 -m venv .venv` : creates a virtual Python environment
   - `source .venv/bin/activate` : opens the virtual Python environment
   - `python3 -m pip install pandas==1.4.3 notebook==6.3.0 elasticsearch==8.7.0` : installs required Python libraries
   - `docker run --rm -p 9200:9200 -p 9300:9300 -e "xpack.security.enabled=false" -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:8.7.0 ` : runs an ElasticSearch container through Docker
4) Open JupyterNotebook locally
5) Run through the code in the `elastic_search_engine.ipynb` file

To run the search engine (Windows):
1) Open the command prompt
2) Install and open Docker Desktop 
2) Run the following commands:
   -  `python -m venv code_search_venv` : creates the virtual Python environment
   -  `code_search_venv\Scripts\activate` : opens the created virtual environment
   -  `pip install -r requirements.txt` : installs necessary dependencies
   -  `docker run --rm -p 9200:9200 -p 9300:9300 -e "xpack.security.enabled=false" -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:8.7.0 ` : runs an ElasticSearch container through Docker
3) Open Jupyter Notebook (make sure you are using the created virtual Python environment)
4) Run the code in the `elastic_search_engine.ipynb` file

To evaluate:
1) `cd notebooks`
2) `evaluation\relevanceeval.py evaluation\annotation_store.csv predictions\ltr_es_model_predictions.csv`

Within the `elastic_search.ipynb`, there are a few areas the user can modify code (view the commented out sections)
- use a smaller subset of the data
- create their own embeddings