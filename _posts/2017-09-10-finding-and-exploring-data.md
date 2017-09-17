---
layout: post
title: "Finding and Exploring Data"
date: 2017-09-10
---
“Those who can’t find the data are doomed to recreate it.”
That may not be quite the quote we all remember but it describes a common situation in organizations with increasing amounts of data in a range of formats. If no one can find an existing data set – how can they be expected to reuse it? This installment of our data engineering series looks at a couple of new solutions to the challenge of finding the data you want and understanding the data that is available.

The first paper is from a research group at Google. It describes a new internal tool called Goods that uses crawling to find data sets within the organization. Goods then organizes a central searchable metadata repository about the data sets that it found.

This solves one of the core issues in understanding what data is available. Its dynamic nature. New data sets are constantly being created and old ones disappearing or changing. What we’ve seen is that trying to create a strict process requiring new data sets to be centrally registered never works. Like requiring developers to do documentation, it either never gets done or never gets kept up to date. Goods allows data set creators to update or enhance the description or metadata about their data set but in never requires that they do this.

In our Alyx solution we discovered that ranking the search results when someone was searching for a particular data set was critical. It simply wasn’t good enough to return the names of every data set that contained a search term such as “Deferred Revenue.” The Google Goods team addressed this by ranking the data sets according to how often they were used and by what processes. They were also able to leverage the Google Knowledge Graph in order to understand the semantics of search terms and the meanings of data. We’re looking at some of the Azure Cognitive Services to possibly add a similar capability to Alyx .

The second paper in today’s discussion comes from a different perspective. Microsoft built an internal application called Guider that focuses on the use of what they call “dependency-driven analytics” in understanding large volumes of unstructured data. They used a graph database to store the relationships between this network of data sets.

One of their most interesting insights is that the graph of relationships served as a sort of “map” to the enormous range of data sets. A way to explore what data is available without having to absorb all of its detail. We’ve also found that displaying graph data using force-directed techniques is a powerful visualization technique.
The authors indicate that the project got its start in trying to assess compliance with auditing and regulatory requirements but has since grown into other use cases. The paper describes several of these use cases including understanding what will be impacted by a failure.

Both of these papers present new approaches and perspectives to the challenges of Finding specific data and Exploring the range of data that is available. They also demonstrate the scalability of an approach based on crawling and consumed data exhaust rather than mandating the creation of metadata through a data governance process. This supports the approach we took with Alyx to have the software do the work rather than the humans.
