# HueControlWebAssemblyExample

HueControlWebAssemblyExample is a web service that allows a user to control Philips Hue lights by providing a SingalR Hub that a locally running client connects to receive cues. 

The application is a basic POC with much of the logic and state hardcoded. While it works over the internet without any firewall or network configuration, it requires that the house with the Hue lights be running the this [WPF/Console Application](https://github.com/olaafrossi/HueControlExample)

<p align="center">
<img src="https://github.com/olaafrossi/HueControlWebAssemblyExample/blob/master/Imgs/HueServer1.PNG"
  alt="UI image"
</p>

* **Uses WebAssembly & Blazor Server** and is cross-platform **linux-windows-docker**.
* Currently limited to 2 Cue buttons.
* Contains basic SignalR chathub for testing- clients can send and receive chat messages from the server and vice-versa. Using for logging, as the buttons are hard-coded to send as user "LD" (Lighting Designer).

## How it works

1. HueControlWebAssemblyExample uses the basic dotnetcore blazor template, and adds one NuGet package `Microsoft.AspNetCore.SignalR.Client` in addition to the         boilerplate that comes with the template.
2. Currently, the application has been tested as an [Azure App Service](https://azure.microsoft.com/en-us/services/app-service) new users get $200 or so of free credit. However, the application can be run in Kestral, IIS, Docker, etc. These configurations (except for a local version Kestral during development) have not been tested, however. 
3. Once the service is running, copy the URL given to you be azure (or, if you setup locally, the address from IIS or Kestral and copy-paste that to the [WPF/Console Application](https://github.com/olaafrossi/HueControlExample)

## How to get it running locally

1. Use VS2019 & and the [dotnetcore 3.1 hosting bundle](https://download.visualstudio.microsoft.com/download/pr/9b9f4a6e-aef8-41e0-90db-bae1b0cf4e34/4ab93354cdff8991d91a9f40d022d450/dotnet-hosting-3.1.6-win.exe)
2. Open the solution in VS2019 and select `HueControlWebAssemblyExample.Server` as the startup project. The combobox for running it should default to "Kestral", but it can run in IIS Express or Kestral. The advantage of Kestral, among others, is that the port remains the same, while IIS Express picks a random port each time you debug the solution. 
3. Refer to the readme here to connect the client to the server [WPF/Console Application](https://github.com/olaafrossi/HueControlExample)

## How to get it running on the Web

1. The simplest way is to generate a new publishing profile with your Microsoft account and create an [Azure App Service](https://azure.microsoft.com/en-us/services/app-service)
2. First, Restore/Update all NuGet packages. Use the GUI for this, `Project -> Manage NuGet Packages -> Install/Restore`
3. Now create your publish profile: Click `Build` and select publish `HueControlWebAssemblyExample.Server`

<p align="center">
<img src="https://github.com/olaafrossi/HueControlWebAssemblyExample/blob/master/Imgs/HueServer3.PNG"
  alt="You will need to create a new profile"
</p>

<p align="center">
<img src="https://github.com/olaafrossi/HueControlWebAssemblyExample/blob/master/Imgs/HueServer5.PNG"
  alt="Choose target type"
</p>

<p align="center">
<img src="https://github.com/olaafrossi/HueControlWebAssemblyExample/blob/master/Imgs/HueServer6.PNG"
  alt="Setup Name, Subscription, Resource Group, and Hosting Plan"
</p>