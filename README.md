[![Version](https://img.shields.io/nuget/v/MudBlazor.Markdown?style=plastic)](https://www.nuget.org/packages/MudBlazor.Markdown/)
[![Nuget downloads](https://img.shields.io/nuget/dt/MudBlazor.Markdown?label=nuget%20downloads&logo=nuget&style=plastic)](https://www.nuget.org/packages/MudBlazor.Markdown/)  
# Markdown component for [MudBlazor](https://github.com/Garderoben/MudBlazor)

This README covers configuration steps for Blazor Server and Blazor WebAssembly. For images how the markup component looks like in the browser go to the [README of samples](/samples).

## Getting started
Install the NuGet package.
```
dotnet add package MudBlazor.Markdown
```
Add the following using statement in `_Imports.razor`.
```razor
@using MudBlazor
```
Add the following nodes in either `App.razor` or `MainLayout.razor`.
```razor
<MudThemeProvider />
<MudDialogProvider />
<MudSnackbarProvider />
```
Add the following nodes in `Pages/_Host.cstml` (Server) or `wwwroot/index.html` (WebAssembly).  
In the `<head>` node add these CSS stylesheets.
```html
<link href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap" rel="stylesheet" />
<link href="_content/MudBlazor/MudBlazor.min.css" rel="stylesheet" />
<link href="_content/MudBlazor.Markdown/MudBlazor.Markdown.min.css" rel="stylesheet" />
```
At the bottom of the `<body>` node add this JS source.
```html
<script src="_content/MudBlazor/MudBlazor.min.js"></script>
```
Register MudBlazor services in the DI container.  
For the Blazor Server in the `Startup.cs` add this method.
```cs
public void ConfigureServices(IServiceCollection services)
{
    services.AddMudServices();
}
```
For the Blazor WebAssembly in the `Program.cs` add this method.
```cs
var builder = WebAssemblyHostBuilder.CreateDefault(args);
builder.Services.AddMudServices();
```
## Using the component
```razor
<MudText Typo="Typo.h3">My markdown</MudText>
<MudMarkdown Value="@Value" />

@code
{
    private string Value { get; } = "text *italics* and **bold**";
}
```
### Available properties
- `Value` - string value of the markdown text;
- `LinkCommand` - `<MudLink>` components will not navigate to the provided URL, but instead invoke the command. If the `LinkCommand` is `null` then `<MudLink>` will navigate to the link automatically (behaviour of `<a>`).
### Palette (colour) configurations
The `<MudMarkdown>` supports the palette of the `MudTheme` which makes styling easy (we hope). The palette can be configured as described [here](https://mudblazor.com/customization/theming/overview). These are the colors which are used in the `<MudMarkdown>`:
- DrawerBackground - background-color of the quoted text;
- OverlayDark - background-color of the code block;
- TextDisabled - border-color of the quoted text and border-color of the h1 and h2 bottom divider;
- TextPrimary - regular text in the markdown;
- TextSecondary - color of the quoted text;
