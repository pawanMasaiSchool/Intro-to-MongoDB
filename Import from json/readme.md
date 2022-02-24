Do the following queries

1) top 10 purchased items
db.productsData.find({}).sort({no_of_purchases:-1}).limit(10)


2) top 10 cheapest items
db.productsData.find({}).sort({price:1}).limit(10)


3) top items where qty remains in stock
db.productsData.find({qty_left:{$gte:1}}).count()
1000
db.productsData.find({qty_left:{$gte:1}})


4) top 10 rated products
db.productsData.find({}).sort({product_rating:-1}).limit(10)


5) bottom 10 rated products
db.productsData.find({}).sort({product_rating:1}).limit(10)


6) from 11-20 top rated products
db.productsData.find({}).sort({product_rating:-1}).skip(10).limit(10)


7) find products with rating between 3 and 4, and sorted from descending order of rating, if the ratings are same, then show the alphabetic order of name of the product

db.productsData.find({product_rating:{$in:[3,4]}}).sort({product_rating:-1,product_name:1}).count()
178
db.productsData.find({product_rating:{$in:[3,4]}}).sort({product_rating:-1,product_name:1})