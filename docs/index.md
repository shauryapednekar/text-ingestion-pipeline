### Goal
The goal of this project is to design and implement a python package that lets
the user easily ingest a textual dataset into a vectorstore.

To that end, this package is focused more on the tooling layer than the actual
application layer. While it lets you easily ingest a dataset into a 
vectorstore, it is highly recommended to override the default loading and 
chunking functions, since application performance relies heavily on those two
steps. See the usage guide for more information on how to write custom classes
for these steps.

Here is the link to the GitHub repo: [https://github.com/shauryapednekar/text-ingestion-pipeline](https://github.com/shauryapednekar/text-ingestion-pipeline)

### Priorities

1. Convenience:  Ingest a dataset in just a few lines of code.
2. Performance: Use multiprocessing where applicable to fully leverage your compute's capabilities. [^1]
3. Customizability: Easily override the default loading, chunking, and embedding functions.
4. Modularity: Use the loader, chunker, and embedder functionality separately if needed.
5. Extendability: Heavy documentation and tests.

Key design principles

1. Avoid re-inventing the wheel: Leveraged open source libraries (mainly LangChain[^2]).
2. DRY (Don't Repeat Yourself): Organized code in order to provide modularity and prevent duplication. 


##### Footnotes

[^1]: More work can be done to allow this package to fully leverage multiple GPUs. See the *Future Work* section.

[^2]: However, I have come to realize that the convencience provided by LangChain's wrappers are sometimes *not* worth the limitations it enforces :) .