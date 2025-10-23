# Examples

The `ballerinax/azure.ai.search.index` connector provides practical examples illustrating usage in various scenarios. Explore these [examples](https://github.com/ballerina-platform/module-ballerinax-azure.ai.search.index/tree/main/examples), covering use cases with client creation, document search operations.

1. [Document search](https://github.com/ballerina-platform/module-ballerinax-azure.ai.search.index/tree/main/examples/document-search) - Search for documents in an Azure AI Search index with various query parameters and filters.

## Prerequisites

1. Generate an API key as described in the [Setup guide](https://central.ballerina.io/ballerinax/azure.ai.search.index/latest#setup-guide).

2. For each example, create a `Config.toml` file the related configuration. Here's an example of how your `Config.toml` file should look:

    ```toml
    serviceUrl = "<YOUR_AZURE_AI_SEARCH_SERVICE_URL>";
    apiKey = "<YOUR_AZURE_AI_SEARCH_API_KEY>";
    indexName = "<YOUR_SEARCH_INDEX_NAME>";
    ```

## Running an example

Execute the following commands to build an example from the source:

* To build an example:

    ```bash
    bal build
    ```

* To run an example:

    ```bash
    bal run
    ```

## Building the examples with the local module

**Warning**: Due to the absence of support for reading local repositories for single Ballerina files, the Bala of the module is manually written to the central repository as a workaround. Consequently, the bash script may modify your local Ballerina repositories.

Execute the following commands to build all the examples against the changes you have made to the module locally:

* To build all the examples:

    ```bash
    ./build.sh build
    ```

* To run all the examples:

    ```bash
    ./build.sh run
    ```
