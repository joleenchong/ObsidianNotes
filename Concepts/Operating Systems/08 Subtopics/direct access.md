A file is made up of a fixed length of logical records that allows programs to read & write in no order.
- based on disk model -> allows random access to any file block
Users provide relative block number -> an index relative to beginning of file. This access method is usually for databases.

Common operations: (note: n = block number)
- read *n* OR position to *n* followed by read next
- write *n* OR position to *n* followed by write next


