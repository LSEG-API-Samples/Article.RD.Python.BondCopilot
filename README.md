# [Bond Copilot: Unleashing Refinitiv Data Library Search API with AI (LLM) - LangChain Python library](https://developers.refinitiv.com/en/article-catalog/article/bond-copilot--unleashing-rd-lib-search-api-with-ai-llm-langchain)
This script assists in searching for specific bond information using a series of filters and queries. It utilizes Large Language Model (LLM) such as ChatGPT that being used in this example to help generate the necessary queries based on user input.

### Disclaimer
The source presented here as well as the example code provided has been written by Refinitiv, an LSEG business for the only purpose of illustrating an article published on the Developer Community. They have not been tested for usage in production environments. Refinitiv cannot be held responsible for any issues that may happen if these objects or the related source code is used in production or any other customer's environment.

### Introduction
The Refinitiv Data Library (RD Library) Search API extends its capabilities to LSEG desktop users, enabling them to programmatically explore an expansive repository of high-quality financial content, spanning various asset classes such as bonds, equities, FX, organizations, individuals, and more. A comprehensive tutorial on utilizing the RD Library Search API has been meticulously crafted by Nick Zincone, available here.

Large Language Models (LLMs) such as OpenAI's GPT, Meta's Llama2, and Google's Bard are sophisticated AI models that have been extensively trained on vast textual datasets. They possess the ability to discern patterns in natural language, generate coherent text, and provide insights across a wide spectrum of subjects.

LangChain emerges as an open-source integration framework designed to seamlessly connect LLM models with external data sources and environments. It facilitates the interaction between LLMs and their surroundings, enhancing their versatility.

The Copilot concept, pioneered by Microsoft in the age of Large Language Models, seeks to create a harmonious and collaborative interplay between human and machine intelligence. It aspires to forge a fluid synergy where both entities complement each other's strengths.

In this article, we embark on an exploration of a Bond Copilot solution powered by an integration of RD Library Search API, LLM, and Langchain, which provides a conversational bond consulting service that can potentially help financial professionals unlocking productivity.

## Prerequisites
- LSEG Workspace application with an access for RD library desktop session, or RDP account for platform session
- An API key generated by App Key application in Workspace.
- Select an LLM from Hugging Face or request access to the OpenAI API
   - As we're using ChatGPT, an AI-powered language model developed by OpenAI in this article, follow steps below to get an Open AI API key  
     1) In Open API Platform, click on your profile (Personal) > View API keys  
     2) Click "Create new secret key" button  
     3) Enter an API key name then click "Create secret key" button  
     4) Copy the API key generated to be used (Do not share the API key with others and please note that they don't display your secret API key again after you generate it)
- Python 3.9 or above
- Python libraries
  - LangChain
  - Refinitiv Data library

## Architecture
![image](https://github.com/Refinitiv-API-Samples/Article.RD.Python.BondCopilot/assets/89068039/3058a488-716f-459b-8270-6a85ba2e2953)

### LangChain Coordination
To smoothly handle multi-turn conversations, Bond Copilot incorporates Langchain to coordinate the interaction between the front-end nature language query and LLM, maintaining context and directing prompts to large language models. Langchain removes the complexity of conversing with AI, making the technology more practical and scalable.

### Large Language Model
Under the hood, Bond Copilot leverages large language models to understand the context and intent and convert nature language query into RD Library Search API.

### RD Library Search API
To enable robust AI insights, Bond Copilot connects to LSEG's RD Library Search API. This provides direct access to LSEG's vast fixed income information including real-time pricing, reference data and more. By leveraging comprehensive, timely data, the quality of Copilot's analytics is significantly enhanced.

## Conversational Search
### Define you bond search function
To begin, it is imperative to craft a bond search function named 'ws_bond_search,' harnessing the capabilities of the RD Library Search API. We could potentially employ the function outlined in the subsequent comments to acquire bond metadata, an essential step in formulating the API search function. The variable 'query' assumes a pivotal role, serving as the conduit for stipulating the criteria for retrieving bond-related information.
For more detail regarding RD library and how to configure it, please check the [Getting started with Refinitiv Data Library for Python guide](https://developers.refinitiv.com/en/api-catalog/refinitiv-data-platform/refinitiv-data-library-for-python/quick-start#getting-started-with-python)

## Intelligent Bond Analytics and Statistics
After filtering a small bond dataset based on the conditions specified by user using 'bond_copilot' function, the utilization of the LangChain Dataframe Agent comes into play for extended analysis and statistical exploration. This step aids users in acquiring deeper insights.

Below is orchestra diagram of LangChain Agent components.
![image](https://github.com/Refinitiv-API-Samples/Article.RD.Python.BondCopilot/assets/89068039/81ed0d4b-661c-457f-b32d-0b19b79eb745)

In LangChain Python documentation regarding LangChain Dataframe Agent, it is noted that “this agent calls the Python agent under the hood, which executes LLM generated Python code - this can be bad if the LLM generated Python code is harmful. Use cautiously”. Nonetheless, it is important to underline that this agent offers substantial analytical conveniences, making it worthwhile to showcase its capabilities in the current phase, albeit with a smaller dataset.

**Step 1:** Initiating the LangChain Dataframe Agent with the query outcome derived from the 'bond_copilot' input and creating LangChain Dataframe Agent.
Or you can replace OpenAI with your preferred LLM (form langchain.llms import <your preferred LLM>)
## Summary and Outlook
Within the context of this article, we present a groundbreaking solution - the Bond Copilot - and illustrate how it harnesses the immense potential of large language models in conjunction with the LangChain framework. The objective is to empower users with the ability to seamlessly navigate a vast array of over 12 million trust bond instruments data using natural language. Furthermore, we showcase the utilization of the LangChain Agent for meticulous bond data analysis. Despite the strides made, the realm of complex bond markets remains rife with challenges.

Relying upon the outputs of large language models within the financial sector is not without its intricacies. Delays in data updates, the limited financial domain acumen of these models, and the difficulty in verifying responses - as these models invariably generate an answer, even if erroneous - all contribute to the complexity.

Consequently, the provision of high-quality financial data by LSEG (London Stock Exchange Group) is pivotal in rendering LLM (large language model) services to financial professionals. The RD Library Search API emerges as a robust avenue for accessing an expansive repository of fixed income data, encompassing real-time prices, reference data, and furnishing AI-driven analyses with precise, up-to-the-minute data.

The solution detailed within this article underscores the LLM's specialization in natural language processing tasks, thereby harnessing its inherent proficiency. The insights, derived from the LSEG's trusted data repository via the RD Library Search API, fortify the responses generated.
Utilizing a conversational interface rather than a traditional search user interface allows customers to directly manipulate data through natural language. This avoids complex UI operations and makes it easier and more efficient for customers to use data.

It is imperative to acknowledge that larger LLM isn't invariably synonymous with better, as considerations regarding the associated costs necessitate prudence. For instance, small models with 6 or 7 billion parameters, through fine-tuning, can still be utilized to address specific business challenges at a lower cost and tried both GPT 3.5 and Llama 7B in this case.

The ascent of large language models has indubitably revolutionized our interaction with financial data. The fusion of natural language comprehension with these models has simplified the information acquisition process for analysts. By enabling them to pose inquiries and receive intricate insights into financial markets, the advent of advanced AI tools grounded in LLM technology is dynamically reshaping the roles of financial analysts, investors, and risk managers. This paradigm shift enhances their capacity to navigate complex information with heightened efficiency and efficacy.

## Reference
- [LSEG Workspace](https://www.refinitiv.com/en/products/refinitiv-workspace/)
- [Refinitiv Data library](https://developers.refinitiv.com/en/api-catalog/refinitiv-data-platform/refinitiv-data-library-for-python) and [it's quick start guide for Python](https://developers.refinitiv.com/en/api-catalog/refinitiv-data-platform/refinitiv-data-library-for-python/quick-start#getting-started-with-python)
- [OpenAI API](https://platform.openai.com/)
- [LangChain](https://python.langchain.com/docs/get_started/introduction)
- For any questions related to the RD library usage, feel free to visit or ask you question in the Developers Community [Q&A Forum](https://community.developers.refinitiv.com/index.html).
