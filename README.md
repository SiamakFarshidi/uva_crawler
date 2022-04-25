# UVA crawler
The UVA crawler is an indexing pipeline that automatically extracts web contents and assigns values to a set of metadata features, incorporating information retrieval techniques including web crawling, metadata extraction, language models, human in the loop, and topic modeling to identify semantic features similarities and generate indexing documents. The UvA pipeline is adjusted based on extendable rules and domain keywords, and domain experts observe and monitor their impacts on the mapping quality. 

# Configuring the crawler
To configure the pipeline, the "config.json" file should be modified to collect the required features from each webpage of the target website. The keys of the "config.json" file are explained as follows. 

## "seed": 
A Seed URL in web crawling is a URL from which a web crawler will begin to traverse a site. Once a crawler is on a seed URL, it will extra data from the page and look for links to additional pages. If a crawler is set to crawl an entire domain, it will systematically follow each link on every page, extracting data from each subsequent page. Paths from a seed URL are often influenced by a website Robots.txt file, which dictates how the site owner would like bots to traverse the site. 

For example: 

    "seed": "https://catalog.data.gov/group/older-adults-health-data"
    

## "permitted_urls_rules": 
It should contain rules based on regular expressions to indicate patterns in URLs. The crawler employs such patterns to extract data from the matched URLs.

For example: 

    "permitted_urls_rules": [https:\\/\\/data.world\\/(.+?)\\/(.*?)*-(.*?)*-(.*?)$"]

## "denied_urls_rules":
It should contain rules based on regular expressions to indicate patterns in URLs. The crawler employs such patterns to **avoid** extracting data from the matched URLs.

For example: 

    "denied_urls_rules": ["https:\\/\\/www.icpsr.umich.edu\\/web\\/HMCA\\/studies\\/\\d{5}$"]


## "render_html":
 Most modern websites contain JavaScript, making them dynamic and interactive. If you try to crawl a website built with Angular, you will not get very far (literally). In order to 'see' the HTML of a web page (and the content and links within it), the crawler needs to process all the code on the page and render the content. Rendering is a process carried out by the browser, taking the code (HTML, CSS, JS, etc...) and translating this into the visual representation of the web page you see on the screen. If you set "render_html" equal to "true", the Chrome driver will be used to render the crawled content first, and then the data extraction process will be performed.
 
 For example: 

    "render_html": true

## "keep_parameters":
If the target website uses URL parameters for insignificant page variations (for instance, color=red vs. color=green), or if it uses parameters that can show essentially the same content using different URLs (for example, example.com/shirts?style=polo,long-sleeve and example.com/shirts?style=polo&style=long-sleeve), the crawler might be crawling the website inefficiently. So, all such parameters will be eliminated by default. However, if you set "keep_parameters" equal to "true", query strings (parameters) of URLs would not be removed. 

 For example: 
 
    "keep_parameters": true

## "keep_parameters_for_indexing":
This property should be set as " true " if you want to force the crawler to extract data based on parameters and store original URLs (including query strings or parameters).

 For example: 

    "keep_parameters_for_indexing": true
    
## "page_counter":
This property can be used for the cases in which the web pages of a website should be crawled based on a page counter in their URLs.

 For example: 

    "page_counter": [https://catalog.data.gov/dataset?page={counter}]

## "start_page_counter_from":
It indicates the starting point of the page counter. Typically, it should be an integer number greater than or equal to zero.

For example: 

    "start_page_counter_from": 1,

## "equal_crawled_features":
This property indicates which metadata feature(s) should be used as the unique identifier to prevent duplicate indices. In most cases, the URL of a webpage can be considered the unique identifier. However, some websites use query strings or parameters to distinguish web contents and create web pages and their contents automatically.

For example: 

    "equal_crawled_features": [
      "url"
    ],



