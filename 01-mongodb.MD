# MongoDB

MongoDB is a popular NoSQL database designed for handling large volumes of unstructured or semi-structured data. Instead of using tables like in traditional SQL databases, MongoDB stores data in flexible, JSON-like documents.

## 🗃️ SQL vs NoSQL (MongoDB) Comparison

| Feature                     | SQL (Relational DB)                           | NoSQL (MongoDB - Document DB)                      |
|----------------------------|-----------------------------------------------|----------------------------------------------------|
| **Data Structure**         | Tables with rows and columns                  | Collections with JSON-like documents (BSON)        |
| **Schema**                 | Rigid schema (must define columns)            | Dynamic schema (schema-less, flexible)             |
| **Query Language**         | SQL (Structured Query Language)               | MQL (MongoDB Query Language - JavaScript style)    |
| **Best Use Cases**         | Banking, ERP, CRM, complex relational systems | Real-time analytics, IoT, content management, apps |
| **Examples**               | MySQL, PostgreSQL, Oracle, SQL Server         | MongoDB, CouchDB, Amazon DocumentDB                |

**Example Document:**

```json
{
  "_id": "6638fa12345abc",
  "name": "Alice",
  "age": 30,
  "skills": ["Java", "DevOps"],
  "address": {
    "city": "Hyderabad",
    "zip": "500001"
  }
}
```

Developer has chosen the database MongoDB. Hence, we are trying to install it up and configure it. 

**Versions of the DB Software you will get context from the developer, Meaning we need to check with developer.**
**Developer has shared the version information as MongoDB-7.x**

Setup the MongoDB repo file 

``` shell title=/etc/yum.repos.d/mongo.repo
[mongodb-org-7.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/9/mongodb-org/7.0/x86_64/
enabled=1
gpgcheck=0
```

Hint! You can create file by using **`vim /etc/yum.repos.d/mongo.repo`**

Install MongoDB 

```shell 
dnf install mongodb-org -y 
```

Start & Enable MongoDB Service 

```shell 
systemctl enable mongod 
systemctl start mongod 
```

Usually MongoDB opens the port only to `localhost(127.0.0.1)`, meaning this service can be accessed by the application that is hosted on this server only. However, we need to access this service to be accessed by another server, So we need to change the config accordingly.

Update listen address from 127.0.0.1 to 0.0.0.0 in `/etc/mongod.conf`

You can edit file by using **`vim /etc/mongod.conf`**

Restart the service to make the changes effected.

```shell 
systemctl restart mongod
```
