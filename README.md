# UVA crawler

The UVA crawler is an indexing pipeline to address these three challenges, incorporating information retrieval techniques including web crawling, metadata extraction, language models, human in the loop, and topic modeling to identify semantic similarities and generate indexing documents. The proposed pipeline is adjusted based on extendable rules and domain keywords, and domain experts observe and monitor their impacts on the mapping quality. 

# Configuring the crawler
To configure the pipeline, the "config.json" file should be modified to collect the required features from each webpage of the target website. The keys of the "config.json" file are explained as follows. For the sake of simplicity, the keys are described based on configuring the crawler for "https://catalog.data.gov/" website.

