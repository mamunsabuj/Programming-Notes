# MERN Stack Notes 
### Install Yarn Globally
  - npm install -g yarn
### Update Yarn
  - yarn set version latest


# MongoDB Basic commands
```
show dbs
use "name"
db.products.insertOne({name: 'Xiomi Note 7', price: '20000'})
 db.products.find()
cls for clear
db.products.find().pretty()
db.products.insertMany([{name: 'vivo', price: '15000'}, {name: 'vivo2', price: '16000'}])
db.products.find({price: '20000'}).pretty()
db.products.find({price: '20000'}, {price: 0}).pretty()
db.products.find({price: '20000'}, {price: 0}).pretty().limit(1)
db.products.find({price: '20000'}, {price: 0}).pretty().limit(1).skip(1)
db.products.findOne({price: '20000'})
```
### update
```
db.products.updateOne({name: 'Xiomi Note 7'}, {$set: {price: 30000}})
db.products.updateMany({}, {$set: {price: 30000}})
`````
### Delete

```
db.products.deleteOne({name: 'vivo2'})
db.products.deleteMany({})
```
