## What is this ?
A implementing json web token  and Proceted Route node js 

## Installation

Run    `npm i joshua-procted-route`

Use :
...

import requireLogin from 'joshua-procted-route'
...

Then...

...

module.exports = (req, res, next) => {
    const { authorization } = req.headers

    if (!authorization)
    {
        return res.status(401).json({ error: "you must be logged in" })
    }
    const token = authorization.replace("Bearer ", "")
    jwt.verify(token, "your Screct key for jwt", (err, payload) => {
        if (err)
        {
            return res.status(401).json({ error: "you must be logged in" })
        }

        const { _id } = payload
        "your schema".findById(_id).then(userdata => {
            req.user = userdata
            next()
        })


    })
}






## Parameters
A implementing json web token  and Proceted Route node js 