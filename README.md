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

create new class by adding a .cs file.

`List<T>.Add(new class<T> {property<T> = string<T>});` adds a new item into a list with certain porperty. For example, it can be used to add a new todo list item with user input string as title. See [CShareNote](https://github.com/Martian42/CSharpeNotes/wiki/Home/_edit#how-to-create-a-class-with-properties)

`<NavLink>` component is provided by Blazor. Components can be used from components by spacifying an element with the component's type name along with attributes for any component parameters. It is the same as an anchor tag, except that is adds an `active` class if the current URL matches the link addess.

`<NavLinkMatch.All` means that the link should be active only when it matches the entire current URL (not just a prefix).


## Basic Blazorapp file structure

- `BlazingPizza.Client`: This is the Blazor project named "BlazingPizza". It contains the UI components for the app.
- `BlazingPizza.Server`: This is the ASP.NET Core project hosting the Blazor app and also the backend services for the app.
- `BlazingPizza.Shared`: This project contains the shared model types for the app.
- `BlazingPizza.ComponentsLibrary`: This is a library components and helper code to be used by the app.

The `BlazingPizza.Server` project should be set as the startup project.

### How to display data from the backend
To get data we need to call an API on the backend. Blazor provides a preconfigured `HttpClient` through dependency injection that is already setup with the correct base address. Uses the `@inject` directive to inject an `HttpClient` into the `Index` component right after `@page "/"`. i.e. `@inject HttpClient HttpClient`

The first token `HttpClient` specifies the property type and the second token specifies the property name.

### Layout for an app
Layouts are also `.razor` components in Blazor. They inherit from `LayoutComponentBase`, which defines a `Body` property that can be used to specify where the bosy of the layout should be rendered. The layout component is typcial located in Shared/MainLayout.razor.

To apply this default layout, look at the `<Router>` component in `App.razor`. Notice that the `DefaultLayout` parameter determines the layout used for all pages unless this is overrided on a per-page basis by adding a directive such as `@layout SomeOtherLayout` at the top of any `.razor`
 page component.
 
 ## Useful example
### A list of cards using `foreach` loop
> <div class="main">
    <ul class="pizza-cards">
        @if (specials != null)
        {
            @foreach (var special in specials)
            {
                <li style="background-image: url('@special.ImageUrl')">
                    <div class="pizza-info">
                        <span class="title">@special.Name</span>
                        @special.Description
                        <span class="price">@special.GetFormattedBasePrice()</span>
                    </div>
                </li>
            }
        }
    </ul>
</div>

https://github.com/dotnet-presentations/blazor-workshop/blob/main/docs/02-customize-a-pizza.md
