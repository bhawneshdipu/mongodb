# mongodb

# get the distinct count

        db.getCollection('data').aggregate([
            {
                $match: {
                    created_at: {
                        $gt: ISODate("2018-07-11T00:00:00.000Z"),
                        $lt: ISODate("2018-07-14T00:00:00.000Z")
                    }
                }
            },
            {
                $group: {
                    _id: "$host"
                }
            },
            {
                $group: {
                    _id: null,
                    distinctCount: { $sum: 1 }
                }
            }
        ])


        db.data.find({'host':'google.com'})


        db.data.aggregate([{$match : {}},{$group:{
        _id: "$host",
        date : { $min: '$created_at' },
        total: { $sum: 1}
        }}, { $match: { total : 1, date : {$gte :ISODate("2018-07-13T00:00:00Z")}}}],{allowDiskUse: true})
        //.match(qb.where("status").eq("A"))
        //.project("gender _id")
        //.unwind("$arrayField")
        //.group({ _id: "$gender", count: { $sum: 1 } })
        //.sort("-count")
        //.limit(5)


                db.contest.aggregate([
                    {"$group" : {_id:"$province", count:{$sum:1}}}
                ])
                db.user.group({
            "key": {
                "province": true
            },
            "initial": {
                "count": 0
            },
            "reduce": function(obj, prev) {
                if (true != null) if (true instanceof Array) prev.count += true.length;
                else prev.count++;
            }
        });
        
        db.test.aggregate({
          $group: {
            _id: '$name',
           name : { $first: '$name' }
           age : { $first: '$age' },
           sex : { $first: '$sex' },
           province : { $first: '$province' },
           city : { $first: '$city' },
           area : { $first: '$area' },
           address : { $first: '$address' },
           count: { $sum: 1 }
          }
        }
        
        dbh.person_document.aggregate([
    {'$unwind': '$phones'},
    {'$group': {
        '_id': '$phones',
        'matchedDocuments': {
            '$push':{
                'id': '$_id',
                'name': '$full_name'
                }},
        'num': { '$sum': 1}
    }},
    {'$match':{'num': {'$gt': 1}}}
        ])

        db.getCollection('RAW_COLLECTION').aggregate([
          // Group on unique value storing _id values to array and count 
          { "$group": {
            "_id": { RegisterNumber: "$RegisterNumber", Region: "$Region" },
            "ids": { "$push": "$_id" },
            "count": { "$sum": 1 }      
          }},
          // Only return things that matched more than once. i.e a duplicate
          { "$match": { "count": { "$gt": 1 } } }
        ], { allowDiskUse: true } )
https://www.mkyong.com/mongodb/mongodb-group-count-and-sort-example/
        { $match: { 
            keywordGroupId: 75, 
            date: {$gte: ISODate("2013-01-01T00:00:00.0Z"), $lt: ISODate("2013-02-01T00:00:00.0Z")}
        }},
