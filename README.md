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
