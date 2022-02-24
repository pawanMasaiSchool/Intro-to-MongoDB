1) find all movies which are equal to movie_name

db.movies_data.find({movie_name:"Tampopo"},{movie_name:1,production_year:1,_id:0})


2) find all movies which are not equal to movie_name
db.movies_data.find({movie_name:{$ne:"Tampopo"}},{movie_name:1,production_year:1,_id:0})


3) find all movies greater than and greater than equal to a budget
db.movies_data.find({budget:{$gte:11000}},{movie_name:1,production_year:1,_id:0}).count()
415
db.movies_data.find({budget:{$gte:11000}},{movie_name:1,production_year:1,_id:0})


4) find all movies less than and less than equal to a budget
db.movies_data.find({budget:{$lte:15000}},{movie_name:1,production_year:1,_id:0})


5) find all movies that are produced after 2000 with budget greater than 10000
db.movies_data.find({$and:[{budget:{$gt:10000}},{production_year:{$gt:2000}}]},{movie_name:1,production_year:1,_id:0}).count()
293
db.movies_data.find({$and:[{budget:{$gt:10000}},{production_year:{$gt:2000}}]},{movie_name:1,production_year:1,_id:0})


6) find all movies that are produced after 2000 or budget greater than 10000
db.movies_data.find({$or:[{budget:{$gt:10000}},{production_year:{$gt:2000}}]},{movie_name:1,production_year:1,_id:0}).count()
487
db.movies_data.find({$or:[{budget:{$gt:10000}},{production_year:{$gt:2000}}]},{movie_name:1,production_year:1,_id:0})



7) find all movies that are neither produced after 2000 nor with budget greater than 10000.
db.movies_data.find({$and:[{budget:{$lte:10000}},{production_year:{$lte:2000}}]},{movie_name:1,production_year:1,_id:0}).count()
13
db.movies_data.find({$and:[{budget:{$lte:10000}},{production_year:{$lte:2000}}]},{movie_name:1,production_year:1,_id:0})


8) find all movies that are not produced in 2000 or they do not have budget of 10000
db.movies_data.find({$or:[{budget:{$ne:10000}},{production_year:{$ne:2000}}]},{movie_name:1,production_year:1,_id:0}).count()
500
db.movies_data.find({$or:[{budget:{$ne:10000}},{production_year:{$ne:2000}}]},{movie_name:1,production_year:1,_id:0})


9) find all movies that were produced from 2000 to 2010.
db.movies_data.find({$and:[{production_year:{$gte:2000}},{production_year:{$lte:2010}},]},{movie_name:1,production_year:1,_id:0}).count()
178
db.movies_data.find({$and:[{production_year:{$gte:2000}},{production_year:{$lte:2010}},]},{movie_name:1,production_year:1,_id:0})

10) Sort all movies descending based on the production year and if the year is same then alphabetically for their movie_names
db.movies_data.find({}).sort({production_year:-1,movie_name:1}).count()
500
db.movies_data.find({}).sort({production_year:-1,movie_name:1})


11) in query 10 skip the first 10 entries and fetch the next 5
 db.movies_data.find({}).sort({production_year:-1,movie_name:1}).skip(10).limit(5)

12) remove movie genre from the first 10 movies in query 10.
