
- MongoDB is a **NoSQL database**.
- It stores data in **JSON-like documents** called **BSON** (Binary JSON), rather than in rows and columns.
- It is **schema-less**, which means documents in a collection do not need to have the same structure.
- High performance for big data and unstructured data

|Feature|JSON|BSON|
|---|---|---|
|**Full Form**|JavaScript Object Notation|Binary JSON|
|**Format**|Text-based|Binary (compact and efficient)|
|**Usage**|Data interchange between client & server|Internal storage format for MongoDB|
|**Size**|Usually larger (text representation)|Smaller, more efficient storage|
|**Parsing**|Readable by humans|Not human-readable|
|**Supports Types**|Limited (string, number, boolean, null, object, array)|Extended (string, int, long, double, decimal128, date, timestamp, binary, objectId, array, object, regex, boolean, null, etc.)|
|**Speed**|Slower to parse|Faster to parse in programs|

### Connection

- **MongoDB native driver** (`mongodb` package) → low-level, direct queries.
- **Mongoose** (ODM) → higher-level, easier to define schemas & models.

### Using Mongoose

```Terminal
npm install mongoose
```

```js
mongoose.connect("mongodb://localhost:27017/mydatabase")
  .then(() => console.log("MongoDB Connected"))
  .catch(err => console.error(err));
```

	