---
CS 157C Project
Professor Dr. Suneuy Kim
Team X
    Aniqua Azad 
    Giang Duong
---

* This project will set up and deploy your NoSQL database, adopt replica set of at least three members and sharding strategies.
* Populate your NoSQL database 1.5GB of data from New York Times articles from January 2008 to December 2020 
*   This application uses MongoDB as its NoSQL database. We chose MongoDB for numerous reasons. One, because the API request returns a list of JSON objects, which can be easily stored in the database. Second, examples of MongoDB usage are for product catalogs or content management systems, and that is what our application does—it manages archived NYT articles. 
    Additionally, our application benefits from a NoSQL database instead of RDBMS. The database has over 1.5GB of data which is also sharded across clusters. In a RDBMS, accessing this data would have taken a long time, but with MongoDB indexes and shard keys, running queries is more efficient and getting articles is faster. In the application, no two articles/documents are alike, which is another benefit of a NoSQL database. For example, articles can have a various number of keywords, and there may be some articles which don’t have certain fields that other articles may have. Also, instead of having another collection that holds comments, we’ve embedded comments in their respective articles. If this were a RDBMS, there would be another table to hold foreign keys and the application would have had to use a ‘join’ operation to get the comments.

* Implement  distinct and significant use cases:
    Create
        addArticle()
This method allows the client to add a new article and its metadata to the database. The client enters necessary information like the URL, abstract, keywords, section and subsection names, etc and the application randomly generates _id and automatically sets the publication date as the time the article was added to the database.
    Retrieve
        findArticlesWKeyValue()
This function allows clients to find similar articles with specific keywords. Given a keyword value, this method lists articles that have the matching keyword value. 
        findArticlesNWordCount()
This function finds articles where the word count is  greater than or equal to a number. The number is an input from the user who may need articles of a certain length.
        getTotalWordCountSubsectionName()
Given a section name provided by the client, this function displays the subsection names for the given section and the total word count per subsection.
        readAbstractBasedOnExpr()
This function allows the user to enter an expression, and the output is the abstract that contains the expression.
        findArticlesFromDate()
This function displays articles from a date provided by the client. The client is prompted to choose from a format and they give a date based on the format.
        findOtherArticlesByPerson()
If a client wanted to read or know about other articles written by a person, they would enter the name of that person, and this function would display articles that person has written.
        getTypeOfMaterialAndMultimedia()
This function returns articles of a certain type of material if and only if the article has multimedia content. The type of material is provided by the client.
        getArticle()
This simple function returns an article’s metadata given the URL.
getNMostPopularKeywords()
This function displays the top N keywords of articles. N is an integer provided by the client.
        getArticlesInSections()
This function allows the user to filter which sections they want to read. Only the articles in the list of sections will be displayed.
Update
        updateReadCountForArticle()
Given a URL (which is provided by the user), this function will increment the read_count field by 1 (one). The output is an acknowledgement if the update was successful and the updated document.
        addCommentsToArticle()
This function allows the user to add comments to an article. They provide the URL of the article they want to add comments to; then they input the commenter’s username, comment body, and number of recommendations. The client can input 1 or more comments. The comments field is an array of documents where each document is a comment. The output is an acknowledgement if the update was successful and the updated document.
        addKeywordArticle()
This function allows the client to add 1 keyword to the current list of keywords. They are prompted to enter the name, value and rank of the keyword which is then pushed to the array. The output is an acknowledgement if the update was successful and the updated document.
    Delete
        deleteManyArticlesWithSectionKeywordVal()
This function will delete any articles that are in a given section and have a specific keyword value. The section name and keyword value are inputs by the client. The output is an acknowledgement of how many articles were removed from the database.
        deleteArticleWordReadCount()
This function deletes many articles from the database where the word count is less than X and the read count is less than Y. X and Y are integer values entered by the user and allows the user to remove articles that are not popular. The output is an acknowledgement of how many articles were removed from the database.  
