- Indexes support all different queries. Improve performance of find operations, update and delete and aggregation.

- Interanlly they represented as b-tree. Another version of binary tree, can contain more then 2 children. It performs better in case where a lot of read / update / writes happen.

- maintaining a index is costly. Every insert / delete / update can result in a updating all corresponding indexes. The results are from one machine, in replica with sharding the cost can be more. But read performance improvements are 10th times

- get list of indexes

  db.restaurants.getIndexes()
    there is always an index (unique) on _id field, and you can't drop it. (only on capped collections)

  db.restaurants.dropIndexes()
    delete all indexes except _id

  db.restaurants.stats()
    reset on server restart, but you can see a date

  db.restaurants.aggregate([ { $indexStats: { } }])
    reset on server restart, but you can see a date

  db.restaurants.createIndex()
    
- when creating an index you can specify any field in document or subdocument, you also specify sort direction (1/ -1), which is important for sorting. You can use field which stor different data types.
You can also specify the whole subdocument, in this case during matching it should be exactly matched to document, even order of field metter. In this case index can't be covered. Options just and object with settings. Foreground indexes block whole database for read / write. But they are much faster.