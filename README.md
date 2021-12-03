# Angular 13 Login and Registration with JWT and Web API example

Build Angular 13 Token based Authentication & Authorization Application with Web Api and JWT (including HttpInterceptor, Router & Form Validation).
- JWT Authentication Flow for User Registration (Signup) & User Login
- Project Structure with HttpInterceptor, Router
- How to implement HttpInterceptor
- Creating Login, Signup Components with Form Validation
- Angular Components for accessing protected Resources
- How to add a dynamic Navigation Bar to Angular App
- Working with Browser Session Storage

## Flow for User Registration and User Login
For JWT – Token based Authentication with Web API, we’re gonna call 2 endpoints:
- POST `api/auth/signup` for User Registration
- POST `api/auth/signin` for User Login

You can take a look at following flow to have an overview of Requests and Responses that Angular 13 JWT Authentication & Authorization Client will make or receive.

![angular-13-login-registration-flow](angular-13-login-registration-flow.png)

## Angular JWT App Diagram with Router and HttpInterceptor
![angular-13-login-registration-overview](angular-13-login-registration-overview.png)

For more detail, please visit the tutorial:
> [Angular Login and Registration with JWT and Web API example](https://bezkoder.com/angular-13-jwt-auth/)

## With Spring Boot back-end

> [Angular + Spring Boot: JWT Authentication and Authorization example](https://bezkoder.com/angular-13-spring-boot-jwt-auth/)

## With Node.js Express back-end

> [Angular + Node.js Express: JWT Authentication and Authorization example](https://bezkoder.com/node-js-angular-13-jwt-auth/)

Depending on the backend you choose, you need to open `app/_helpers/auth.interceptor.js`, modify the code like this:
```js
...

// const TOKEN_HEADER_KEY = 'Authorization'; // for Spring Boot back-end
const TOKEN_HEADER_KEY = 'x-access-token';   // for Node.js Express back-end

@Injectable()
export class AuthInterceptor implements HttpInterceptor {
  ...

  intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
    ...
    if (token != null) {
      // for Spring Boot back-end
      // authReq = req.clone({ headers: req.headers.set(TOKEN_HEADER_KEY, 'Bearer ' + token) });

      // for Node.js Express back-end
      authReq = req.clone({ headers: req.headers.set(TOKEN_HEADER_KEY, token) });
    }
    return next.handle(authReq);
  }
}

...
```

Run `ng serve --port 8081` for a dev server. Navigate to `http://localhost:8081/`.

## More practice
> [Angular JWT Refresh Token example with Http Interceptor](https://www.bezkoder.com/angular-12-refresh-token/)

> [Angular CRUD Application example with Web API](https://www.bezkoder.com/angular-13-crud-example/)

> [Angular Pagination example | ngx-pagination](https://www.bezkoder.com/angular-13-pagination-ngx/)

> [Angular File upload example with Progress bar](https://www.bezkoder.com/angular-13-file-upload/)

Fullstack with Node:

> [Angular + Node Express + MySQL example](https://www.bezkoder.com/angular-13-node-js-express-mysql/)

> [Angular + Node Express + PostgreSQL example](https://www.bezkoder.com/angular-13-node-js-express-postgresql/)

> [Angular + Node Express + MongoDB example](https://www.bezkoder.com/mean-stack-crud-example-angular-13/)

> [Angular + Node Express: File upload example](https://www.bezkoder.com/angular-13-node-express-file-upload/)

Fullstack with Spring Boot:

> [Angular + Spring Boot + H2 Embedded Database example](https://www.bezkoder.com/spring-boot-angular-13-crud/)

> [Angular + Spring Boot + MySQL example](https://www.bezkoder.com/spring-boot-angular-13-mysql/)

> [Angular + Spring Boot + PostgreSQL example](https://www.bezkoder.com/spring-boot-angular-13-postgresql/)

> [Angular + Spring Boot + MongoDB example](https://www.bezkoder.com/angular-13-spring-boot-mongodb/)

> [Angular + Spring Boot: File upload example](https://www.bezkoder.com/angular-13-spring-boot-file-upload/)

Fullstack with Django:
> [Angular + Django example](https://bezkoder.com/django-angular-13-crud-rest-framework/)

Serverless with Firebase:
> [Angular Firebase CRUD with Realtime DataBase | AngularFireDatabase](https://www.bezkoder.com/angular-13-firebase-crud/)

> [Angular Firestore CRUD example with AngularFireStore](https://www.bezkoder.com/angular-13-firestore-crud-angularfirestore/)

> [Angular Firebase Storage: File Upload/Display/Delete example](https://www.bezkoder.com/angular-13-firebase-storage/)

Integration (run back-end & front-end on same server/port)
> [How to integrate Angular with Node Restful Services](https://bezkoder.com/integrate-angular-12-node-js/)

> [How to Integrate Angular with Spring Boot Rest API](https://bezkoder.com/integrate-angular-12-spring-boot/)
