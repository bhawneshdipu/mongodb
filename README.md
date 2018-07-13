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


