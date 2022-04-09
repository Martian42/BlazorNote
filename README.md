# BlazorNote
*My Cheatsheet when using Blazor* 😂
## Project set up
### Build your Blazor app
[Download and install](https://dotnet.microsoft.com/en-us/learn/aspnet/blazor-tutorial/install)

[Create the app](https://dotnet.microsoft.com/en-us/learn/aspnet/blazor-tutorial/create)

### Basic syntax
`@code` directive to add multiple line of codes enclosed by parentheses.

`@Page` directive is a special markup that identifies a component as a page. Use this directive to specify a route. i.e. `@Page "/todo"`

`@bind` is used to bind a C# variable to an HTML object. You define the C# variable by name as a string in the HTML.

Create a **new page** with `dotnet new razorcomponent -n Todo -o Pages`. Razor component file names require a capitalized first letter. Open the Pages folder and confirm that the component file name starts with a capital letter.

`List<T>.Add(new class<T> {property<T> = string<T>});` adds a new item into a list with certain porperty
