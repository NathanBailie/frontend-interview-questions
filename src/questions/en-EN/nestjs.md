<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/nestjs.png">
  <h2>NestJs</h2>
</div>
<br />

<details>
<summary><span>1. What is <b>NestJS</b>?</span></summary>
<br />

**NestJS** is a **framework for Node.js** built with **TypeScript** and inspired by **Angular’s architecture**. It helps create **scalable server-side applications** using **modules**, **controllers**, and **services**, supports **dependency injection**, and integrates easily with **Express** or **Fastify**.

</details>

---

<details>
<summary><span>2. What is <b>middleware</b>?</span></summary>
<br />

**Middleware** is a **function** that **intercepts a request** between the client and the controller. It can perform **logging**, **authentication**, **validation**, modify the request, or terminate it before passing it further. In NestJS, it's connected via `@Middleware()` or `app.use()`.

</details>

---

<details>
<summary><span>3. What’s the <b>difference between Nest middleware and Express middleware</b>?</span></summary>
<br />

**Express middleware** is a simple function `(req, res, next)` registered manually via `app.use()`.

**NestJS middleware** is a **class with a `use()` method**, registered via **modules** and **`MiddlewareConsumer`**, supports **dependency injection**, and integrates better with Nest’s architecture.

</details>

---

<details>
<summary><span>4. What is <b>dependency injection</b>?</span></summary>
<br />

**Dependency Injection (DI)** is a pattern where **dependencies (services, classes, data)** are passed into a component **from the outside**, rather than being created inside it. This simplifies **testing**, **scalability**, and **loose coupling**. In NestJS, it’s implemented via **decorators** and an **inversion of control container**.

</details>

---

<details>
<summary><span>5. What <b>decorators</b> are available in NestJS?</span></summary>
<br />

NestJS uses decorators to define components and their behavior:

- **@Module** – defines a module and its dependencies
- **@Injectable** – makes a class available for DI
- **@Controller** – defines a controller and its routes
- **@Get**, **@Post**, **@Put**, **@Delete** – HTTP route handlers
- **@Body**, **@Param**, **@Query**, **@Headers** – access parts of the request
- **@UseGuards**, **@UseInterceptors**, **@UseFilters** – attach guards, interceptors, and filters
- **@Catch** – exception handling
- **@Pipe** – create custom pipes

</details>

---

<details>
<summary><span>6. What is an <b>event emitter</b>?</span></summary>
<br />

In **NestJS**, you can use an **EventEmitter** via the `@nestjs/event-emitter` package. It allows you to define **events** and **listeners**, so components can **react to actions** without being directly coupled. Useful for **logging**, **notifications**, and **internal communication** between modules.

</details>

---

<details>
<summary><span>7. <b>Guards, Pipes, Interceptors</b></span></summary>
<br />

In NestJS, these elements handle requests at different stages:

- **Guards** – determine whether a route can be executed (e.g., authorization). Use `@UseGuards`.
- **Pipes** – transform and validate incoming data (`@Body`, `@Param`, etc.). Use `@UsePipes`.
- **Interceptors** – intercept requests/responses, add logic (logging, caching, timing). Use `@UseInterceptors`.

All three are powerful tools for **preprocessing**, **security**, and **extending route behavior**.

</details>

---

<details>
<summary><span>8. Which runs first – <b>guard or middleware</b>?</span></summary>
<br />

**Middleware** runs **before** **guards**.  
Request lifecycle in NestJS:

1. **Middleware** – registered via `app.use()` or `MiddlewareConsumer`, runs before routing
2. **Guards** – run after routing, determine access
3. **Interceptors**, **Pipes**, **Controllers** – follow next in the chain

So middleware handles early logic like logging or parsing, while guards handle access control.

</details>

---

<details>
<summary><span>9. What is the <b>request lifecycle</b> in NestJS?</span></summary>
<br />

The request lifecycle in NestJS includes several stages:

1. **Middleware** – first interception (e.g., logging, body parsing)
2. **Guards** – access control and authorization
3. **Interceptors (before)** – logic before controller execution (e.g., timing, transformation)
4. **Pipes** – validation and transformation of input
5. **Controller** – main request handler
6. **Service** – business logic called from the controller
7. **Interceptors (after)** – post-processing of the response
8. **Exception Filters** – error handling if something goes wrong

This structure allows fine-grained control over request handling.

</details>

---

<details>
<summary><span>10. How does Nest handle <b>errors</b> during request processing?</span></summary>
<br />

NestJS uses **Exception Filters** for centralized error handling. By default, it uses `HttpException`, which returns a structured response with a status code and message.

You can also create **custom filters** using the `@Catch()` decorator to handle specific errors and return custom responses.  
Filters can be applied:

- Globally (`app.useGlobalFilters()`)
- At the controller level
- At the method level

This gives you flexible control over how errors are handled in your app.

</details>

---

<details>
<summary><span>11. How does <b>reflect-metadata</b> work?</span></summary>
<br />

`reflect-metadata` is a library that allows you to **store and retrieve metadata** on classes, methods, and parameters.  
It’s used in **TypeScript** and heavily in **NestJS** for working with **decorators** like `@Injectable()`, `@Controller()`, etc.

Examples:

- `Reflect.defineMetadata(key, value, target)` – stores metadata
- `Reflect.getMetadata(key, target)` – retrieves metadata

This enables Nest to **automatically wire dependencies**, **build routes**, and **perform validation**.

</details>

---

<details>
<summary><span>12. How to solve <b>circular dependency</b> in NestJS?</span></summary>
<br />

A circular dependency occurs when two or more providers depend on each other directly or indirectly. In NestJS, you can resolve it using:

- **`forwardRef(() => Class)`** – defers resolving the dependency until all modules are loaded

  Example:

  ```ts
  @Injectable()
  export class ServiceA {
  	constructor(
  		@Inject(forwardRef(() => ServiceB)) private serviceB: ServiceB
  	) {}
  }
  ```

- **Extracting shared logic into a separate module** – helps break the cycle
- **Refactoring architecture** – sometimes circular dependencies indicate overly tight coupling

</details>

---

<details>
<summary><span>13. What is the purpose of the <b>CQRS pattern</b>?</span></summary>
<br />

**CQRS (Command Query Responsibility Segregation)** is a pattern that separates **read operations (Query)** and **write operations (Command)** into different models and handlers.

It’s used for:

- 🔹 **Scalability** – read and write paths can be optimized independently
- 🔹 **Simplified business logic** – commands change state but don’t return data
- 🔹 **Clear separation of concerns** – cleaner, more maintainable code
- 🔹 **Flexibility** – different data sources can be used for reads and writes

In NestJS, CQRS is implemented using **CommandHandlers** and **QueryHandlers**, typically via the `@nestjs/cqrs` package.

</details>

---

<details>
<summary><span>14. Why do we use <b>entities</b> in NestJS?</span></summary>
<br />

An **Entity** is a class that defines the **structure of a database table**.  
It’s used with **TypeORM**, **Prisma**, or other ORMs for:

- 🔹 Defining fields and relationships (columns, types, associations)
- 🔹 Connecting the database with TypeScript code
- 🔹 Auto-generating SQL queries
- 🔹 Validating and transforming data at the model level

In NestJS, entities are the foundation for working with **repositories**, **services**, and **DTOs**, ensuring clean architecture and strong typing.

</details>

---

<details>
<summary><span>15. What is an <b>I/O container</b> in Next.js?</span></summary>
<br />

An **I/O container** is a component or module that manages **input and output of data** between the client and server. It can:

- 🔹 Accept input (requests, parameters, forms)
- 🔹 Process it (API calls, database queries)
- 🔹 Return results (page rendering, JSON responses)

In modern versions of Next.js, this role is often handled by **Server Actions** and **Route Handlers**, which connect client components to server logic.

</details>

---

<!-- <details>
<summary><span><b></b></span></summary>
<br />

</details>

--- -->
