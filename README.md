# firelete examples

Examples demonstrating how to use [firelete](https://github.com/JonnyOrman/firelete).

It contains the following examples:
- `example1` - deletes documents with string IDs
- `example2` - deletes documents with int IDs
- `example3` - config retrieved from the environment
- `example4` - config retrieved from both the config file and the environment
- `example5` - uses the Docker image

# How to run

With Docker installed, clone the repo and run
```
docker-compose up --build
```

Go to the Firestore emulator at `localhost:4000/firestore/data`, create a collection called "MyCollection", and add some documents to it.

To use each of the examples, `POST` to the following:
- `example1` - `localhost:3001`
- `example2` - `localhost:3002`
- `example3` - `localhost:3003`
- `example4` - `localhost:3004`
- `example5` - `localhost:3005`

Include the `Content-Type` header set to `application/json` and a body that looks like this:
```
{
    "message": {
        "data": "ewogICAgImRvY3VtZW50SUQiOiAiYWJjIgp9"
    }
}
```

The `data` value must be a JSON object with a `documentID` value in Base64 format, where the `documentID` value is the ID of the document to delete. The above example `data` is for the following JSON object, where the `documentID` value is "abc":
```
{
    "documentID": "abc"
}
```

For `example2` the `documentID` must be a numeric value. For example:
```
{
    "documentID": 123
}