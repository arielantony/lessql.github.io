# LESSQL Framework Home Page

Here you will find discussions about the LESSQL framework!

Our [dataset](https://github.com/anonymousyouser/LESSQL/blob/master/dataset.zip) is currently available!

All of our experiments were executed on a machine with the following specifications:

Machine | Specifications
------- | --------------
CPU | Intel Core i7 7700 3.4GHz
Memory | 32GB
Hard Disk | 1TB
OS Distribution | Linux Ubuntu Bionic Beaver 18.04
Python | Python 3.4

## Dataset Limitations

I. There are possible threats related to the representativeness of a single dataset. Thus, we tried to select a dataset which is representative of how structural schema changes are made across a certainly reasonable number of closed-source and open-source projects. For instance, the number of attributes that suffered modifications in a single schema change is not usually high in the dataset. However, this scenario is representative of how schemas structurally change over time in many projects: structural schema changes are made incrementally in order to avoid constant major refactoring, for instance, in the affected source code. On the other hand, there were big changes in the dataset as well. For instance, version 21 suffered the biggest schema change, which have 27 attribute modifications all together. Moreover, while the dataset may not cover all possible categories of structural change categories,  it clearly covers various categories with a certain frequency (as illustrated in the paper). Finally, this dataset covers 4 years of development in the Wikipedia project and is representative for all the problems we tackle, since it went through a high diversity of schema structural changes.

II.	Another limitation of our study was the number of relations for all schema versions of the Wikipedia dataset. Our Joining Network Expression generation algorithm (JNG) computes the joining network expressions (JNE) according to the changes in the target schema. As said in (I), since we worked with a relatively small number of schema changes per schema version, LESSQL may have been limited to structural refactoring changes in a few tables. Nevertheless,  [Qiu] suggests that only a minor portion of the schema is changed over the lifetime of a database. Also, the generation time depends directly on the number of tables involved in the schema changes. In this dataset, the longest time was 39 seconds for a query that referred to 9 attributes. Overall, our JNE generation approach can be considered as a specification of the Steiner Tree Problem in which we must find the shortest interconnection between relations that contain all attributes from a LESSQL query. The Steiner Tree Problem is said to be NP-Complete so our JNG algorithm uses a heuristic approach, which can be improved in the future.

## Metrics Limitations

III. One of the threats relates to the chosen metric for evaluating the stability of the system (schemas, queries and surrounding source code). One could question the choice of only using Success Rate as a measure of such stability. However, the obtained results were based on the Success Rate (SR) of SQL query generation, that is, whether LESSQL was able to successfully generate an SQL query that could be executed over the target schema [with corresponding semantic]. The SR metric shows that  SQL queries could be successfully generated for the target schema. As a consequence, the correct generation of SQL queries would enable developers to avoid application source code maintenance, which is a key purpose of this approach. Therefore, the use of SR indeed quantifies the stability of schemas and queries, while it also serves as a surrogate, reliable metric for code stability. As the SR of two configurations was often higher than 95%, then no code change is required for most of the schema changes.

IV.	We do not measure how the adoption of LESSQL affects development processes, including code comprehension tasks. Certain query and surrounding code changes might become more difficult when the queries are written with LESSQL. For instance, we do not know how the syntax of LESSQL may interfere in how developers understand the query and surrounding code. This is actually a concern that should be addressed in the near future. Nevertheless, we should recall that the syntax of LESSQL is the same as the syntax of SQL with the exception of not including the “from” clause on it.

## Solution Limitations

V. Depending on the type and number of changes, the SchemaDiff algorithm may struggle to find the correct attribute mappings. For example, an attribute previously named "person” renamed to “identification” is a significant change since SchemaDiff relies on syntactic similarity. However, as discussed in the paper, this situation can be circumvented by using the hybrid or supervised configurations.
