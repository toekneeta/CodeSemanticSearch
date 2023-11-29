# CodeSemanticSearch
A semantic search engine that takes in natural language queries and outputs Python functions corresponding to the queries. Uses data from the CodeSearchNet challenge.

The search engine uses ElasticSearch to store and search through the Python functions, its code, documentation, and other related attributes. Uses LambdaRank to re-rank the initial ElasticSearch results.

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
