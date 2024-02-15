## Now with Pandas

Perform the same text processing with Pandas.
From a Notebook.
And save results into a sqlite3 database.

To do that, you'll need to think about the dataframe you need to create.
What columns does it have?

How do you make a relationship between the document data (the name, the word count, the lines and char counts) and the frequencies.

Probably two tables, word_freq and letter_freq?
Or can you think of a better way to turn the data into a _schema_?
