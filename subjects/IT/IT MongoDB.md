---
alias: MongoDB
definition: a source-available, cross-platform, document-oriented database program
type: document-oriented-database
subject: database
more-info: "https://en.wikipedia.org/wiki/MongoDB"
---
[[IT database]]

| commands                                                                                                                                      | info                                                  |
| --------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| `mongo --port 27117 ace --eval "db.admin.find().forEach(printjson);"`                                                                         | show all records in database ace                      |
| `mongo --port 27117 ace --eval 'db.admin.update({"_id": ObjectId("61ce278f46e0fb0012d47ee4")},{$set:{"x_shadow":"SHA_512 Hash Generated"}})'` | update a record in database ace based on the ObjectId |
