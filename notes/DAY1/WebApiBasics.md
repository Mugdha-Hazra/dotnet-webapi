
# 1. What Is an API?

**API** stands for **Application Programming Interface**.

An API is a **set of rules and methods** that allows **one software application to talk to another**.

Think of it as:

> A **contract** that says:
> “If you send me data in this format, I’ll give you data in that format.”

### Simple Meaning

An API lets you use someone else’s system **without seeing how it works internally**.

You only know:

* What to send
* What you’ll get back

You don’t know:

* Their code
* Their database
* Their servers
* Their logic

And you **don’t need to know**.

---

# 2. What Is a Web API?

A **Web API** is an API that works **over the internet** using **HTTP**.

So:

> **Web API = API + Internet + HTTP**

It means:

* You send a request using HTTP
* Over the web
* To another application
* And get a response

Example:

```
Your App  →  Internet  →  Web API  →  Response
```

---

# 3. What Is HTTP?

**HTTP (HyperText Transfer Protocol)** is a set of rules for sending data on the web.

It defines:

* How requests are sent
* How responses are returned
* What format data should use
* How errors are handled

### Example HTTP Request

```
GET /users/1
```

Means:

> “Give me data of user 1”

### Example HTTP Response

```
200 OK
{
  "name": "John",
  "age": 25
}
```

Means:

> “Here is the data you asked for”

So HTTP is the **language of communication** on the web.

---

# 4. Real-Life Example: Electricity Socket

This example is very important.

### In Your House

When you charge your phone:

* You plug into a socket
* Phone starts charging
* You don’t know how electricity is produced
* You don’t know wiring
* You don’t know power stations

You just use it.

### Mapping to APIs

| Real World    | Software World       |
| ------------- | -------------------- |
| Socket        | API                  |
| Electricity   | Data / Functionality |
| Phone         | Client App           |
| Power Station | Server / Backend     |

So:

> The **API is like a socket**.

It hides complexity.

---

# 5. Why APIs Are Important

APIs provide:

### ✅ Abstraction

You don’t see internal logic.

### ✅ Security

Users cannot access your database directly.

### ✅ Reusability

Many apps can use the same API.

### ✅ Scalability

You can change backend without changing clients.

---

# 6. API Consumer vs API Creator

### 1️⃣ API Consumer

When you **use someone else’s API**.

Example:

* Google Maps API
* Payment Gateway API
* Weather API

You send requests → get responses.

### 2️⃣ API Creator

When **you build your own API** so others can use it.

Example:

* You build a backend for your app
* Other apps connect to it

Most professional developers do **both**.

---

# 7. Web API Architecture (Big Picture)

![Image](https://substackcdn.com/image/fetch/%24s_%21g3db%21%2Cf_auto%2Cq_auto%3Agood%2Cfl_progressive%3Asteep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4a38175b-11e8-40ae-879c-ab3ce2027089_2008x1252.png)
<img width="1183" height="634" alt="image" src="https://github.com/user-attachments/assets/d56d12a3-df09-47ec-8628-5c03e3778acd" />
<img width="1345" height="537" alt="image" src="https://github.com/user-attachments/assets/878fa74a-a9c3-48c0-ab4c-f69b3337899d" />
<img width="901" height="631" alt="image" src="https://github.com/user-attachments/assets/089f163b-fb77-4025-ae4c-d629bd320ac9" />
</br>![Image](https://voyager.postman.com/illustration/diagram-rest-postman-illustration.svg)

A typical Web API system has **three layers**:

```
Client  →  Web API  →  Database
```

Let’s understand each.

---

## 7.1 Client Applications (Frontend)

These are apps that users interact with.

Examples:

* Web apps
* Mobile apps
* Desktop apps

Their job:

* Show UI
* Take user input
* Send requests to API
* Display results

They **never talk to the database directly**.

Why?
👉 Security risk.

---

## 7.2 Web API (Backend / Server)

This is the **core brain**.

It sits in the middle.

### Responsibilities

The API:

1. Receives HTTP requests
2. Validates data
3. Checks authentication
4. Runs business logic
5. Talks to database
6. Sends response

So it acts as a **mediator**.

### Example

Client sends:

```
POST /register
{
  "email": "abc@gmail.com",
  "password": "1234"
}
```

API does:

* Validates email
* Hashes password
* Saves in DB
* Returns success

---

## 7.3 Data Storage (Database)

This is where data is stored permanently.

Examples:

* Users
* Orders
* Products
* Payments

Databases use **SQL** or similar languages.

The client **never** connects here directly.

Only the API can.

---

# 8. Why We Need a “Translator” (Entity Framework Core)

Your API is written in **C#** (or some language).

Your database understands **SQL**.

They don’t speak the same language.

So we need a **translator**.

That translator is:

> **Entity Framework Core (EF Core)**

---

## 8.1 What Is Entity Framework Core?

EF Core is an **ORM (Object-Relational Mapper)**.

ORM means:

> It converts **Objects ↔ Tables**

### It maps:

| C#       | Database |
| -------- | -------- |
| Class    | Table    |
| Property | Column   |
| Object   | Row      |

---

## 8.2 Example Without EF Core

Without EF Core, you write SQL manually:

```sql
SELECT * FROM Users WHERE Id = 1;
```

Then parse results in C#.

Harder.
More errors.
More code.

---

## 8.3 Example With EF Core

With EF Core:

```csharp
var user = context.Users.Find(1);
```

That’s it.

EF Core:

* Creates SQL
* Executes it
* Converts result to object

Automatically.

---

# 9. Models (C# Classes)

EF Core works using **Models**.

Models are C# classes that represent database tables.

---

## 9.1 Example Model

```csharp
public class User
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }
}
```

This maps to:

| Column |
| ------ |
| Id     |
| Name   |
| Email  |

---

## 9.2 Relationships in Models

You can define relationships.

Example:

One user → many orders

```csharp
public class User
{
    public int Id { get; set; }
    public List<Order> Orders { get; set; }
}
```

EF Core understands:

> One-to-Many relationship

And creates foreign keys.

---

# 10. Request → Processing → Response Flow

Let’s see the full journey.

---

## Step 1: Client Sends Request

Example:

```
GET /api/users/1
```

Using HTTP.

---

## Step 2: API Receives Request

The API:

* Checks URL
* Matches route
* Calls controller method

Example:

```csharp
[HttpGet("{id}")]
public User GetUser(int id)
```

---

## Step 3: API Validates

It checks:

* Is user authenticated?
* Is ID valid?
* Do they have permission?

---

## Step 4: API Talks to Database

Using EF Core:

```csharp
var user = context.Users.Find(id);
```

EF Core → SQL → Database → Result → Object

---

## Step 5: API Creates Response

API converts object to JSON:

```json
{
  "id": 1,
  "name": "John"
}
```

---

## Step 6: Client Receives Response

Client displays data.

Done.

---

# 11. HTTP Request Types (Methods)

Different actions use different HTTP methods.

| Method | Purpose     |
| ------ | ----------- |
| GET    | Read data   |
| POST   | Create data |
| PUT    | Update data |
| DELETE | Remove data |

Example:

```
GET    /users        → Get users
POST   /users        → Add user
PUT    /users/1      → Update
DELETE /users/1      → Delete
```

This is called **RESTful API design**.

---

# 12. HTTP Response Types

Each response has:

### 1️⃣ Status Code

| Code | Meaning      |
| ---- | ------------ |
| 200  | OK           |
| 201  | Created      |
| 400  | Bad Request  |
| 401  | Unauthorized |
| 404  | Not Found    |
| 500  | Server Error |

### 2️⃣ Body (Data)

Usually JSON.

Example:

```json
{
  "success": true,
  "message": "User created"
}
```

---

# 13. Why This Architecture Is Used

This architecture is used because:

### ✅ Separation of Concerns

Frontend ≠ Backend ≠ Database

### ✅ Easy Maintenance

Change DB → frontend unaffected

### ✅ Multiple Clients

Same API works for:

* Web
* Mobile
* Desktop

### ✅ Scalability

Can handle millions of users

### ✅ Security

No direct DB access

---

# 14. Complete Flow (Summary)

Let’s summarize everything:

```
User
 ↓
Frontend (Client)
 ↓ HTTP
Web API (C#)
 ↓ EF Core
Database (SQL)
 ↑
Response (JSON)
 ↑
Frontend
 ↑
User sees data
```

---

# 15. In Simple Words

If I explain everything in one paragraph:

> A Web API is a middleman between your app and your database. Your app sends HTTP requests to the API. The API processes them, talks to the database using Entity Framework Core, converts database records into C# objects, and sends the result back as JSON. The client never sees the internal code, just like you never see how electricity is produced—you just use the socket.

---

