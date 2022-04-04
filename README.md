# UVA crawler

The UVA crawler is an indexing pipeline to address these three challenges, incorporating information retrieval techniques including web crawling, metadata extraction, language models, human in the loop, and topic modeling to identify semantic similarities and generate indexing documents. The proposed pipeline is adjusted based on extendable rules and domain keywords, and domain experts observe and monitor their impacts on the mapping quality. 

# Configuring the crawler
To configure the pipeline, the "config.json" file should be modified to collect the required features from each webpage of the target website. The keys of the "config.json" file are explained as follows. For the sake of simplicity, the keys are described based on configuring the crawler for "https://catalog.data.gov/" website.

## "seed": 
A Seed URL in web crawling is a URL from which a web crawler will begin to traverse a site. Once a crawler is on a seed URL, it will extra data from the page and look for links to additional pages. If a crawler is set to crawl an entire domain, it will systematically follow each link on every page, extracting data from each subsequent page. Paths from a seed URL are often influenced by a website Robots.txt file, which dictates how the site owner would like bots to traverse the site. 

