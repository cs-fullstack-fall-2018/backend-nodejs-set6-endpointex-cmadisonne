# Assignment on adding routes and using conditional searches

* Add an endpoint for ```/api/todo/age/:numdays``` to apiController()
* Use moment date/time package to subtract ```numdays``` from the current date to get the age date
* Return any ToDos that are incomplete *AND* have a create date that is on or before the age date

- Use an HTTP GET for your route endpoint
- You'll need to use Mongoose/Mongo Conditionals for your database query (https://docs.mongodb.com/manual/reference/operator/query-comparison/)

app.get('/api/todos/age/:numdays', function (req, res) {
        // const numdays = 5;
        const age = moment().subtract(req.params.numdays, 'days').calendar();
        Todos.find({dueDate: {$lte:age}}, function (err, todos) {
            if (err) {
                throw err; // If we get an error then bail
            }
            // Use Express to send the JSON back to the client in the web response
            res.send({$and: [{todos:dueDate = 'false'}, {todos:dueDate <= age}]});
        })
    });

