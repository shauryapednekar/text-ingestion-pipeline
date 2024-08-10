### Future Work

Given that my goal was to spend less than a week working on this, tradeoffs were made. I'll highlight the main ones here.

#### Testing

Due to time constraints, I focused on getting the package to a functional state first. This package contains a few unit tests for the `Loader` and `Chunker` classes, but they are by no means exhaustive. I plan on adding more unit tests in the future. 
For integration tests, a few scenarios I think would be worth adding are:

1. Running the ingestion pipeline on the same dataset twice using the same vectorstore [^5].
2. Create a sample dataset of a few sentences that have clear and distinct categories. Ingest this into a vectorstore and perform similarity search, verifying that it returns the expected results.

#### Customizability

Providing more defaults for the Document Loaders, Embedders, and Vectorstores.  Also, providing the ability to easily select a relevance score for the vectorstore would be nice.

Additionally, the ability to load from and write to remote locations (like S3) might be useful depending on the use case.

Lastly, an easy way to disable the progress bar would be nice - something I realized in hindsight. Relatively straightforward fix, but something I realized only recently.

#### Performance

This package doesn't leverage distributed computing/multiple GPUs efficiently right now. It might be worth sharding the dataset and parallelizing the work across available GPUs, or using something like Ray to do this ([example](https://gist.github.com/waleedkadous/4c41f3ee66040f57d34c6a40e42b5969#file-build_vector_store_fast-py-L30)).

###### Footnotes

[^5]: This currently fails due to limitations with Faiss' implementation. Fixing this either requires more custom logic for upserts, or switching to using LangChain's Indexing API. See Faiss' default configuration in `defaults.py` for more.