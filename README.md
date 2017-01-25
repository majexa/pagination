#Pagination

##Installation

    npm install ngn-pagination
    
##Usage example

    var Pagination = require('ngn-pagination');
    var pagination = new Pagination({
      basePath: '/api/v1/users',
      maxPages: 6
    });
    var totalRecordsCount = 100;
    var currentPageN = 1; // first page
    // currentPageN = request.params.pn{N}
    var paginationData = pagination.data(currentPageN, totalCollectionRecordsCount);
    
    // Using result with MongoDB collection
    collection.find({}).
      skip(pagination.options.n * (paginationData.page - 1)).
      limit(pagination.options.n).
      toArray().then(function (items) {
        console.log(items);
      });
    