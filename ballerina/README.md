## Overview

[Azure AI Search](https://azure.microsoft.com/en-us/products/ai-services/cognitive-search) is a cloud search service with built-in AI capabilities. It provides the Azure AI Search REST API to access powerful search and indexing functionality, enabling the creation of rich search experiences.

The Azure AI Search Index connector offers functionality to connect and interact with the Azure AI Search Index Management REST API, allowing seamless interaction with search indexes, documents, and search operations.

### Key Features

- Efficient management of search indexes and documents
- Support for Azure AI Search Index Management REST API
- Intelligent search capabilities with built-in AI
- Seamless integration with Azure's cloud search infrastructure

## Setup guide

To use the Azure AI Search Index Connector, you must have access to Azure AI Search through an Azure account and a search service resource. If you do not have an Azure account, you can sign up for one at the Azure website.

### Create an Azure AI Search Service

1. Open the Azure Portal.

2. Navigate to Create a resource -> AI + Machine Learning -> Search service.

3. Fill in the required details:
   - Resource group
   - Service name
   - Location
   - Pricing tier

4. Review and create the search service.

5. Once the service is deployed, navigate to the service and obtain the service URL and Admin API keys from the "Keys" section.

6. Store the service URL and API key securely to use in your application.

## Quickstart

To use the `Azure AI Search Index` connector in your Ballerina application, update the `.bal` file as follows:

### Step 1: Import the module

Import the `ballerinax/azure.ai.search.index` module.

```ballerina
import ballerinax/azure.ai.search.index;
```

### Step 2: Create a new connector instance

Create an `azure.ai.search.index:Client` with the obtained service URL and API Key and initialize the connector.

```ballerina
configurable string serviceUrl = ?;
configurable string apiKey = ?;
configurable string indexName = "my-test-index";

final index:Client azureSearchIndexClient = check new (string `${serviceUrl}/indexes/${indexName}`);
index:DocumentsSearchGetHeaders headers = {"api-key": apiKey};
```

### Step 3: Invoke the connector operation

Now, you can utilize available connector operations.

#### Search for documents in an index

```ballerina

public function main() returns error? {

    // Search for documents
    index:SearchDocumentsResult searchDocumentsResult = check azureSearchIndexClient->documentsSearchGet(headers,
        api\-version = "2025-09-01",
        search = searchTerm,
        \$count = true,
        \$select = ["content"]
    );
    
    // Process search results
    index:SearchResult[] documents = searchDocumentsResult.value;
    io:println(string`Found ${documents.length()} documents for "${searchTerm}":`);
    foreach index:SearchResult doc in documents {
        io:println(doc.toJsonString());
    }
}
```

### Step 4: Run the Ballerina application

```bash
bal run
```

## Examples

The `Azure AI Search Index` connector provides practical examples illustrating usage in various scenarios. Explore these [examples](https://github.com/ballerina-platform/module-ballerinax-azure.ai.search.index/tree/main/examples/), covering the following use cases:

1. [Document search](https://github.com/ballerina-platform/module-ballerinax-azure.ai.search.index/tree/main/examples/document-search) - Search for documents in an Azure AI Search index with various query parameters and filters.
