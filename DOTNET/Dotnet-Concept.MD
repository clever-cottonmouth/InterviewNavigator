# What are solid principles ?

S- Single responsibility - Each class should have single job/responsibility.
O - Open/Closed Principle. Classes must be open to extension but closed to modification.
L - Liskov principle - If class A is subtype of class B then, Class B should be able to replace Class A with out disrupting the behaviour of our program.
I - Interface segregation - Clients should not be forced to depend on methods that they do not use.
D - Dependency inversion - High level modules should not depend on low level modules. Both must depend on abstraction.

---

# What are DRY, YAGNI, KISS principles ?

DRY- Do not repeat yourself.
Avoid duplication. Makes the software more maintainable and less error-prone.

YAGNI - You are not going to need it.
Avoid unnecessary features/functionalities to the software. This helps software focussed on essential requirements and makes it more maintainable.

KISS: Keep the implementation simple,stupid.
Keeping the software design and implementation as simple as possible.
This make software more understandable,maintainable and testable.

---

---

# Return Type

Return View
Return partial View
Redirect
Redirect To Action
Return content
Return JSON
Return JavaScript
Return File

# Repository Pattern

Design Pattern to separate the data access layer from application

Provides Interface without exposing implementation

Helps create abstraction

## What is the difference between const and readonly in C#?

`const`: Can't be changed anywhere.

`readonly`: This value can only be changed in the constructor. Can't be changed in normal functions.

# FOR AND FOREACH

The foreach statement is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects. If you need to add or remove items from the source collection, use a [for](https://learn.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2008/ch45axte(v=vs.90)) loop.

If you are iterating through a collection of items, and do not care about the index values then foreach is more convenient, easier to write and safer: you can't get the number of items wrong.

If you need to process every second item in a collection for example, or process them ion the reverse order, then a for loop is the only practical way.

# EXTENSION METHODS

Extension method allow us to seemingly add methods to an existing type without modifying this type's source code.

They are static method, but they're called as if they were instance methods on the extended type.

```
namespace Polymorphism.Extensions
{
	public static class StringExtensions
	{
		public static int CountLines(this string input)=> input.Split(Environment.NewLine).Length;
	}
}
```

# CONVENTIONAL AND ATTRIBUTE ROUTING

Following are some suggestions on when to use each one. Consider choosing traditional routes when:

You want centralized configuration of all your routes.
You use custom constraint objects.
You have an existing working application you don't want to change
Consider choosing attribute routes when:

You want to keep your routes together with your action's code
You are creating a new application or making significant changes to an existing.
You want to match route parameter names with an actual parameter of the method(action), this will make the route parameter more descriptive and omit the weird error where the route ID would not match and that usually happens because we didn't configure routing correctly and we were using asp.net default route.
But the reasons why many developers recommend the Attribute Routes is because it allows you quite a bit more flexibility and places the routes next to the actions that will actually use them. You can switch from option to another at any time is not difficult

Attribute Routing
Problems in Conventional Routing

Very difficult to understand for the developers, which route is for which action methods.

Very difficult to avoid conflicts among the routes [some times, we can't apply constraints].

Overall, some routes for multiple action methods; some routes for specific action methods; Overall, it looks cumbersome.

RouteConfig.cs

protected static void RegisterRoutes( RouteCollection routes)
{
   routes.MapRoute("name", "url", defaults, constraints);
   routes.MapRoute("name", "url", defaults, constraints);
   routes.MapRoute("name", "url", defaults, constraints);
   …
}

Types of URL Routing
Conventional Routing

It is the traditional way of routing.  routes.MapRoute( "name", "url", { defaults } )

Applicable for a specific / multiple action methods.

Routes will be cumbersome.

Enabled by default.

Supports parameters & constraints.

Attribute Routing

1. New and preferred way of routing:

["url"]
public ActionResult Methodname( )
{
}
2. Applicable for specific action method. Each action method must have "Route" defined.

3. Routes are very clearly understandable for the developers.
4. Should be enabled using:  routes.MapMvcAttributesRoutes( );
5. Also supports parameters & constraints.

# What is the use of @Html.AntiForgeryToken()?

Let's assume you have a register functionality in your web app. You have an AccountController (example.com/account/register) where you expect people to submit their info. Normally before someone posts the registration information needs to visit the actual (example.com/account/register) than submit the form.

Let say I am a bad guy and I want to flood your server with junk info all I need to do is just keep posting directly to (example.com/account/register) without visiting your site. So in order to stop me you implement AntiForgeryToken so you can make it sure I visited the page before I submitted the registration information.

CSRF / XSRF (Cross Site Request Forgery) is a process of sending a request to actual website, from a page present in attacker website, based on the logged-in session of actual website user.

#### How to Implement CSRF Security?

**View**

`@Html.AntiForgeryToken( )`

**Controller**

<pre class="prettyprint linenums prettyprinted" role="presentation"><ol class="linenums"><li class="L0"><p><span class="pun">[</span><span class="typ">ValidateAntiForgeryToken</span><span class="pun">]</span></p></li><li class="L1" data-node-id="20240810195432-c52y22a"><p><span class="kwd">public</span><span class="pln"></span><span class="typ">ActionResult</span><span class="pln"></span><span class="typ">Method</span><span class="pun">(</span><span class="pln"></span><span class="pun">)</span></p></li><li class="L2"><p><span class="pun">{</span></p></li><li class="L3" data-node-id="20240810195432-p1f8zmf"><p><span class="pun">}</span></p></li></ol></pre>

# Performance Optimization

Bundling and Minification
Used to load multiple css files / js files with a single request.

Also minifies (compresses) the css / js files.

Types of Bundles:

ScriptBundle: Contains javascript files (.js files).

StyleBundle: Contains css fles (.css files).

Microsoft.AspNet.Web.Optimization

This NuGet Package needs to be installed in the project, to use bundling concept.

# Strongly Typed Views

View that is associated to a specific model class is called as "Strongly Typed View".

Strongly typed views have to specify the model class name with @model directive at the top of the view.

Strongly Typed Views can receive model objects from the controller.

To receive model collections from the controller: `@model List<modelClassNameHere>`

# HTML Helpers

@Html.DisplayFor(modelItem => item.Id)

@Html.ActionLink("Edit", "Edit", new { id = item.Id })

* Binds HTML elements to Model Properties.
* Pre-defined methods that execute on server and generate (render) a specific html tag at run time.
* @Html is an object of HtmlHelper class.

**Server code:**

`@Html.TextBoxFor (model => model.EmpName)`

**Browser (Client) - auto generated**

<pre class="prettyprint linenums prettyprinted" role="presentation"><ol class="linenums"><li class="L0"><p><span class="tag"><input</span><span class="pln"></span><span class="atn">type</span><span class="pun">=</span><span class="atv">"text"</span><span class="pln"></span><span class="atn">name</span><span class="pun">=</span><span class="atv">"EmpName"</span><span class="tag">></span></p></li></ol></pre>

#### List of HTML Helpers

1. **Html.ActionLink:**      Hyperlink
2. **Html.TextBoxFor: **    Textbox
3. **Html.TextAreaFor:**   TextArea
4. **Html.CheckBoxFor: **   CheckBox
5. **Html.RadioButtonFor: **  RadioButton
6. **Html.DropDownListFor:**    Dropdown
7. **Html.ListBoxFor:**    Multi-Select ListBox
8. **Html.HiddenFor: **   Hidden Field
9. **Html.PasswordFor: **  Password TextBo
10. **Html.DisplayFor: **   Plain text
11. **Html.LabelFor: **   Label
12. **Html.EditorFor: **  TextBox /    TextArea / Numeric TextBox / Date TextBox etc.

# Built-in Tag Helpers:

* **<a asp-controller=”Home” asp-action=”Index”>Link `</a>`:** Generates a link with a URL that’s generated by routing based on the specified controller and action.
* **<img src=”~/images/pic.jpg” asp-append-version=”true” />:** Generates a `<img>` tag with a cache-busting query string to ensure the latest version of the image is fetched.
* **<form asp-controller=”Account” asp-action=”Login” method=”post”>…`</form>`:** Generates a form element with the appropriate action attribute for the specified controller and action.
* **`<input asp-for=”Username” />`:** Generates an input field with attributes based on the model property specified by asp-for.

# Types of ActionResult

1. ContentResult: Represents any content with specific content-type.
2. ViewResult: Represents result of a view.
3. FileResult: Represents content of a file.
4. JsonResult: Represents json object / json array.
5. RedirectResult: Represents redirection to other website (HTTP 302).
6. RedirectToRouteResult: Represents redirection to a specific action method (HTTP 302).
7. PartialViewResult: Represents the result of partial view.# ActionFilters# Filter

# Filters

Filters Execute at a specific situation, while executing an action method.

**Authentication Filters**

* Executes first, before any other filter, to check whether the user is a valid user or not.
* Implemented using IAuthenticationFilter

**Authorization Filters**

* Executes first, before any other filter, to check whether the user has permission to execute the action method or not.
* Implemented using IAuthorizationFilter

**Action Filters**

* Action filters allow us to execute code before or after the execution of action methods in controllers. Action Filters are useful for handling cross-cutting concerns within an application, such as Logging, Authentication, Authorization, Caching, Exception Handling, etc.
* Implemented using IActionFilter

**Result Filters**

Result Filters are a specific type of filter that runs after the action method has been executed but before the result is processed and sent to the client. This means that with Result Filters, we can modify the view or the result data before it is returned to the client.

OnExecuted

OnExecuting

**Exception Filters**

* Executes when an exception is raised while executing the action method or result. You can store exception log.
* Implemented using IExceptionFilter

# Built-in Filters

**Authorization Filters**

1. **[ChildActionOnly] ** : Accepts only child requests (not direct requests).
2. **[ValidateAntiForgeryToken] ** : Accepts only the requests from same domain. Useful for CSRF security
3. **[Authorize] ** : Accepts only if the user has logged-in.

**Action Filters**

1. **[ActionName]** : Defines name of action, which is different than method name.
2. **[NonAction]** : Defines that the method is not an action method.
3. **[HttpGet] ** : Accepts only GET request.
4. **[HttpPost] ** : Accepts only POST request.
5. **[OutputCache] ** : Caches result of action method & delivers the same for subsequent requests.

# Server Side Validation

**ModelState.IsValid:** Checks whether the model object satisfied all the validation rules

# Client Side Validation

**Three NuGet packages:**

1. jQuery :    Performs DOM manipulations
2. jQuery.Validation :   Defines Validation Rules
3. Microsoft.jQuery.Unobtrusive.Validation:     Shows / Hides Error Message

#### HTML Helpers for Client Side Validation

1. **ValidationMessageFor :**      Displays error message
2. ValidationSummary:             Displays validation summary

#### Custom Validation

* Used to implement user-defined validations.
* Create a class that extends ValidationAttribute class.
* IsValid method executes after submitting the form (after Model Binding).
* IsValid method receives the input value as argument.
* ValidationContext provides details about current model property’s details.
* IsValid method returns either “Success” or “ValidationResult with error message”.
* Best for database related validations.

<pre class="prettyprint linenums prettyprinted" role="presentation"><ol class="linenums"><li class="L0"><p><span class="kwd">public</span><span class="pln"></span><span class="kwd">class</span><span class="pln"></span><span class="typ">SampleAttribute</span><span class="pln"></span><span class="pun">:</span><span class="pln"></span><span class="typ">ValidationAttribute</span></p></li><li class="L1" data-node-id="20240813131529-uiehjz3"><p><span class="pun">{</span></p></li><li class="L2"><p><span class="pln"></span><span class="kwd">protected</span><span class="pln"></span><span class="kwd">override</span><span class="pln"></span><span class="typ">ValidationResult</span><span class="pln"></span><span class="typ">IsValid</span><span class="pun">(</span><span class="kwd">object</span><span class="pln"> value</span><span class="pun">,</span><span class="pln"></span><span class="typ">ValidationContext</span><span class="pln"> validationContext</span><span class="pun">)</span></p></li><li class="L3" data-node-id="20240813131529-mebt7zd"><p><span class="pln"></span><span class="pun">{</span></p></li><li class="L4"><p><span class="pln"></span><span class="com">//your code here</span></p></li><li class="L5" data-node-id="20240813131529-6f59upt"><p><span class="pln"></span><span class="kwd">return</span><span class="pln"></span><span class="typ">ValidationResult</span><span class="pun">.</span><span class="typ">Success</span><span class="pun">;</span></p></li><li class="L6"><p><span class="pln"> </span></p></li><li class="L7" data-node-id="20240813131529-yepqde9"><p><span class="pln"></span><span class="com">//or</span></p></li><li class="L8"><p><span class="pln"></span><span class="kwd">return</span><span class="pln"></span><span class="kwd">new</span><span class="pln"></span><span class="typ">ValidationResult</span><span class="pun">(</span><span class="kwd">this</span><span class="pun">.</span><span class="typ">ErrorMessage</span><span class="pun">);</span></p></li><li class="L9" data-node-id="20240813131529-42mvnyf"><p><span class="pln"></span><span class="pun">}</span></p></li><li class="L0"><p><span class="pun">}</span></p></li></ol></pre>

# What is Asp.Net Core meta package?

The ASP.NET Core shared framework (Microsoft.AspNetCore.App) contains assemblies that are developed and supported by Microsoft. Microsoft.AspNetCore.App is installed when the .NET Core 3.0 or later SDK is installed. The shared framework is the set of assemblies (.dll files) that are installed on the machine and includes a runtime component and a targeting pack.

```
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net6.0</TargetFramework>
  </PropertyGroup>
    ...
</Project>
```

# Middleware

Middleware is a component that is assembled into the application pipeline to handle requests and responses.

Middleware are chained one-after-other and execute in the same sequence how they're added.

Middleware can be a request delegate (anonymous method or lambda expression) [or] a class.

**app.Run( )**

<pre class="prettyprint linenums prettyprinted" role="presentation"><ol class="linenums"><li class="L0"><p><span class="pln">app</span><span class="pun">.</span><span class="typ">Run</span><span class="pun">(</span><span class="pln">async </span><span class="pun">(</span><span class="typ">HttpContext</span><span class="pln"> context</span><span class="pun">)</span><span class="pln"></span><span class="pun">=></span></p></li><li class="L1" data-node-id="20240816162155-p8fwuzv"><p><span class="pun">{</span></p></li><li class="L2"><p><span class="com">//code</span></p></li><li class="L3" data-node-id="20240816162155-cz1eeik"><p><span class="pun">});</span></p></li></ol></pre>

The extension method called “Run” is used to execute a terminating / short-circuiting middleware that doesn’t forward the request to the next middleware.

**app.Use( )**

<pre class="prettyprint linenums prettyprinted" role="presentation"><ol class="linenums"><li class="L0"><p><span class="pln">app</span><span class="pun">.</span><span class="typ">Use</span><span class="pun">(</span><span class="pln">async </span><span class="pun">(</span><span class="typ">HttpContext</span><span class="pln"> context</span><span class="pun">,</span><span class="pln"></span><span class="typ">RequestDelegate</span><span class="pln"></span><span class="kwd">next</span><span class="pun">)</span><span class="pln"></span><span class="pun">=></span></p></li><li class="L1" data-node-id="20240816162204-dlayh8d"><p><span class="pun">{</span></p></li><li class="L2"><p><span class="pln"></span><span class="com">//before logic</span></p></li><li class="L3" data-node-id="20240816162204-o61zhd1"><p><span class="pln">  await </span><span class="kwd">next</span><span class="pun">(</span><span class="pln">context</span><span class="pun">);</span></p></li><li class="L4"><p><span class="pln"></span><span class="com">//after logic</span></p></li><li class="L5" data-node-id="20240816162204-peu7e52"><p><span class="pun">});</span></p></li></ol></pre>

The extension method called “Use” is used to execute a non-terminating / short-circuiting middleware that may / may not forward the request to the next middleware.

#### Middleware Class

Middleware class is used to separate the middleware logic from a lambda expression to a separate / reusable class.

<pre class="prettyprint linenums prettyprinted" role="presentation"><ol class="linenums"><li class="L0"><p><span class="kwd">class</span><span class="pln"></span><span class="typ">MiddlewareClassName</span><span class="pln"></span><span class="pun">:</span><span class="pln"></span><span class="typ">IMiddleware</span></p></li><li class="L1" data-node-id="20240816162226-7pcm3rg"><p><span class="pun">{</span></p></li><li class="L2"><p><span class="pln"></span><span class="kwd">public</span><span class="pln"> async </span><span class="typ">Task</span><span class="pln"></span><span class="typ">InvokeAsync</span><span class="pun">(</span><span class="typ">HttpContext</span><span class="pln"> context</span><span class="pun">,</span><span class="pln"></span><span class="typ">RequestDelegate</span><span class="pln"></span><span class="kwd">next</span><span class="pun">)</span></p></li><li class="L3" data-node-id="20240816162226-e0k0ccv"><p><span class="pln"></span><span class="pun">{</span></p></li><li class="L4"><p><span class="pln"></span><span class="com">//before logic</span></p></li><li class="L5" data-node-id="20240816162226-99u9xl5"><p><span class="pln">    await </span><span class="kwd">next</span><span class="pun">(</span><span class="pln">context</span><span class="pun">);</span></p></li><li class="L6"><p><span class="pln"></span><span class="com">//after logic</span></p></li><li class="L7" data-node-id="20240816162226-gp3g4tr"><p><span class="pln"></span><span class="pun">}</span></p></li><li class="L8"><p><span class="pun">}</span></p></li></ol></pre>

`app.UseMiddleware<MiddlewareClassName>();`

#### The Right Order of Middleware

1. **app**.**UseExceptionHandler**(**"/Error"**);
2. **app**.**UseHsts**();
3. **app**.**UseHttpsRedirection**();
4. **app**.**UseStaticFiles**();
5. **app**.**UseRouting**();
6. **app**.**UseCors**();
7. **app**.**UseAuthentication**();
8. **app**.**UseAuthorization**();
9. **app**.**UseSession**();
10. **app**.**MapControllers**();
11. **//add your custom middlewares**
12. **app**.**Run**();

**app.UseWhen( )**

<pre class="prettyprint linenums prettyprinted" role="presentation"><ol class="linenums"><li class="L0"><p><span class="pln">app</span><span class="pun">.</span><span class="typ">UseWhen</span><span class="pun">(</span></p></li><li class="L1" data-node-id="20240816162333-s46y8rw"><p><span class="pln">  context </span><span class="pun">=></span><span class="pln"></span><span class="pun">{</span><span class="pln"></span><span class="kwd">return</span><span class="pln"></span><span class="kwd">boolean</span><span class="pun">;</span><span class="pln"></span><span class="pun">},</span></p></li><li class="L2"><p><span class="pln">  app </span><span class="pun">=></span></p></li><li class="L3" data-node-id="20240816162333-jkda115"><p><span class="pln"></span><span class="pun">{</span></p></li><li class="L4"><p><span class="pln"></span><span class="com">//add your middlewares</span></p></li><li class="L5" data-node-id="20240816162333-zj23qua"><p><span class="pln"></span><span class="pun">}</span></p></li><li class="L6"><p><span class="pun">);</span></p></li></ol></pre>

The extension method called “UseWhen” is used to execute a branch of middleware only when the specified condition is true.

# Caching

ASP.NET Core supports several types of caching:

* **In-memory Caching:** In this case, data is stored in the web server’s Memory (RAM). This is simple to implement, very fast, and ideal for single-server scenarios.
* **Distributed Caching:** In this case, it uses external cache stores like Redis or SQL Server. This is suitable for applications running on multiple servers in a load-balancing environment.
* **Response Caching:** In this case, it caches the responses of HTTP requests to improve the response time for similar requests. Stores the output of a request and reuses it for similar requests.
