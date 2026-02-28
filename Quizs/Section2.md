<img width="1045" height="400" alt="image" src="https://github.com/user-attachments/assets/897d13f2-3080-464d-84aa-5b0e88fa832d" />
<img width="1053" height="413" alt="image" src="https://github.com/user-attachments/assets/72975780-c5ef-42c9-bcd5-9daad0be9c8b" />
<img width="986" height="404" alt="image" src="https://github.com/user-attachments/assets/e83bbb87-ed74-4cf7-ae3a-3e778d9e0da8" />
<img width="1022" height="445" alt="image" src="https://github.com/user-attachments/assets/0ef7771f-6e7d-4ce0-bb81-57aa624ad6ff" />
<img width="1056" height="405" alt="image" src="https://github.com/user-attachments/assets/49048b30-5929-439d-aadd-3692fe26a1be" />

## 1. ASP.NET Core Web API – **Purpose (Service-Oriented Architecture)**

**Core concept:** **Web services & REST**

ASP.NET Core Web API is built to expose **data and functionality over HTTP** using REST principles.

Key ideas:

* Client–server separation (frontend ≠ backend)
* Stateless communication
* Uses HTTP verbs:

  * `GET` → Read data
  * `POST` → Create data
  * `PUT` → Update data
  * `DELETE` → Remove data

**Why “scalable web services”?**

* Stateless APIs scale easily
* Can be hosted in cloud, containers, or on-prem
* Supports high concurrency and performance

➡️ This is why the correct answer is **to build scalable web services**.

---

## 2. ASP.NET Core SDK – **Development Toolchain**

**Core concept:** **Build + Run + Manage**

The **SDK** is the development toolkit for .NET.

It includes:

* .NET CLI (`dotnet new`, `dotnet run`, `dotnet build`)
* Compilers
* Runtime libraries
* Project templates

Without the SDK:

* You cannot create projects
* You cannot compile code
* You cannot run applications

➡️ That’s why it is required **to write and execute .NET applications**.

---

## 3. Web API Template – **Convention over Configuration**

**Core concept:** **Pre-configured architecture**

The **ASP.NET Core Web API template** sets up best practices automatically:

It includes:

* Controllers (`[ApiController]`)
* Routing
* Dependency Injection
* Middleware pipeline
* Optional Swagger support

This saves time and enforces **standard API structure**.

➡️ Hence, the correct choice is **ASP.NET Core Web API**.

---

## 4. `Startup.cs` – **Application Configuration Pipeline**

**Core concept:** **Middleware + Dependency Injection**

`Startup.cs` defines **how the app starts and handles requests**.

### Two critical responsibilities:

#### 1️⃣ Configure Services

```csharp
services.AddControllers();
services.AddDbContext<MyDbContext>();
```

* Registers dependencies
* Enables DI throughout the app

#### 2️⃣ Configure Middleware

```csharp
app.UseRouting();
app.UseAuthorization();
app.UseEndpoints(...);
```

* Controls request flow
* Each middleware processes HTTP requests in order

**Request pipeline concept:**

```
Request → Middleware → Controller → Response
```

➡️ Therefore, its purpose is **to define middleware and services**.

---

## 5. Swagger – **API Discoverability & Contract**

**Core concept:** **Self-documenting APIs**

Swagger provides:

* API contract (OpenAPI specification)
* Interactive documentation
* Live endpoint testing

Why it matters:

* Frontend developers know how to call the API
* Easy debugging and validation
* Clear request/response models

Example:

* Try `POST /api/products`
* See required fields
* Test directly in browser

➡️ That’s why the answer is **API documentation and testing**.

---

## Core Concepts Summary Table

| Concept              | Why It Matters                           |
| -------------------- | ---------------------------------------- |
| Web API              | Exposes backend logic via HTTP           |
| REST                 | Standard communication model             |
| SDK                  | Enables development and execution        |
| Template             | Pre-built API architecture               |
| Startup.cs           | Configures services and request pipeline |
| Middleware           | Handles requests step-by-step            |
| Dependency Injection | Loose coupling, testability              |
| Swagger              | API documentation & testing              |

---

## Big Picture Architecture

```
Client (Browser / Mobile / App)
        ↓ HTTP
Middleware Pipeline
        ↓
Controllers (Web API)
        ↓
Services / Business Logic
        ↓
Database
```


### **Question 1: What is the primary purpose of ASP.NET Core Web API?**

✅ **Correct Answer: To build scalable web services**

**Explanation:**
ASP.NET Core Web API is designed to create RESTful HTTP services that can be consumed by browsers, mobile apps, and other clients. It focuses on building **scalable, high-performance web services**, not desktop applications or direct database management.

---

### **Question 2: Why is it necessary to install the ASP.NET Core SDK?**

✅ **Correct Answer: To write and execute .NET applications**

**Explanation:**
The **.NET SDK** provides the tools required to:

* Create new projects
* Build applications
* Run applications
* Manage dependencies

Without the SDK, you cannot develop or execute .NET applications.

---

### **Question 3: What template should you select for a new Web API project?**

✅ **Correct Answer: ASP.NET Core Web API**

**Explanation:**
When creating a new project in Visual Studio or using the CLI, selecting the **ASP.NET Core Web API** template sets up:

* Controllers
* Routing
* Middleware configuration
* Swagger support (optional)

This template is specifically structured for building APIs.

---

### **Question 4: What is the purpose of the `Startup.cs` file?**

✅ **Correct Answer: To define middleware and services**

**Explanation:**
In ASP.NET Core (especially pre-.NET 6 structure), `Startup.cs` is used to:

* Configure services (Dependency Injection)
* Configure the HTTP request pipeline (middleware)

It does **not** store data or directly configure databases unless you register database services there.

---

### **Question 5: What does Swagger provide for your API?**

✅ **Correct Answer: API documentation and testing**

**Explanation:**
Swagger (via Swashbuckle in ASP.NET Core) provides:

* Interactive API documentation
* Endpoint descriptions
* Request/response models
* A built-in UI to test API endpoints

It helps developers understand and test APIs easily.

---

### ✅ Overall Summary

This quiz covers the **core building blocks of ASP.NET Core Web API**:

* Web APIs are for building scalable services.
* The .NET SDK enables development and execution.
* The Web API template sets up the correct project structure.
* `Startup.cs` configures services and middleware.
* Swagger documents and tests APIs.




