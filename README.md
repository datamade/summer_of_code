Summer of Code 2014
==============

The Open Data movement represents an enormous opportunity for citizens to understand and monitor what governments and other powerful institutions are up to. 

Unfortunately, most of the time, public data is messy data. In order gain insight from public data, analysts have to figure out which records are about the same thing either within a dataset across datasets.

This problem has been called deduplcation, record linkage, and entity resolution, among other names, and it's subtle and difficult problem. Traditional approaches are very labor intensive, very expensive, or both.

DataMade is the main developer of the open source, python library [dedupe](https://github.com/open-city/dedupe) that solves this problem. We use machine learning and clever algorithms to deduplicate data on an ordinar, modern laptop.

There are a number of enhancements to dedupe that would make a good summer project.

1. **Active learning.** Right now, dedupe uses a simple version of active learning to learn how to effectively and efficiently deduplicate records. Our current technique has two main drawbacks. First, we don't give the user effective feedback on whether they have given us enough labels. Second, our technique has no guarantees that it will give a good results (althought it usually does in practice). We could benefit from recent research breakthroughs in active learning: http://hunch.net/?cat=22
2. **More and Better string distances** At the core, dedupe tries to learn what kinds of similarities between records matter (i.e. does it matter more if the personal names are similar or addresses). This means that better similarity functions can have a huge impact on overall importance. Some of the distancse that we would like to add are simple (tf-idf distance, and some are quite involved and interesting like discriminatively trained conditional random fields.)
3. **Metric trees for candidate selection** In order to compare records efficiently, dedupe needs to only compare records that are likely to be to duplicates. We have some effective methdods to do this now, but we can benefit from more, advanced information retrieval techniques like metric trees or levenshtein automata.
4. **Trainable Tokenizers** Often, the deduplication task would be simplified if records were split into meaningful semantic units. For example, if instead of field like `{"address" : "123 N. Main St, Metropolis, IN, 76064"} we had the fields {"street number" : "123", "street direction" : "N", "street name" : "Main", "street type" : "Street", "city" : "Metropolis", "city" : "Indiana", "zip code" : "76064"}. We would like to investigate learning Hidden Markov Models to create these types of semantic tokenizers for preprocessing.
