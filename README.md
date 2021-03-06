# HueControlWebAssemblyExample

Build Status: 

![.NET Core](https://github.com/olaafrossi/HueControlWebAssemblyExample/workflows/.NET%20Core/badge.svg)

HueControlWebAssemblyExample is a web service that allows a user to control Philips Hue lights by providing a SignalR Hub to which a client connects in order to receive cues to change Hue Lights. 

The application is a basic POC with much of the logic and state hardcoded. While it works over the internet without any firewall or network configuration, it does requires that the house with the Hue lights be running the this [WPF/Console Application](https://github.com/olaafrossi/HueControlExample)

<p align="center">
<img src="https://github.com/olaafrossi/HueControlWebAssemblyExample/blob/master/Imgs/HueServer1.PNG"
  alt="UI image"
</p>

* **Uses WebAssembly & Blazor Server** and is cross-platform **linux-windows-docker**.
* Currently limited to 2 Cue buttons.
* Contains basic SignalR chathub for testing- clients can send and receive chat messages from the server and vice-versa. The chat function is useful for testing and logging, as the buttons are hard-coded to send as user "LD" (Lighting Designer) when pressing the Cue01 or Cue 02 buttons.

## How it works

1. HueControlWebAssemblyExample uses the basic dotnetcore blazor template, and adds one NuGet package `Microsoft.AspNetCore.SignalR.Client` in addition to the boilerplate packages that are bundled with the template.
2. The application has been tested as an [Azure App Service](https://azure.microsoft.com/en-us/services/app-service) new users get $200 or so of free credit. However, the application can be run in Kestral, IIS, Docker, etc. These configurations (except for local Kestral on the same network (standard class C LAN) during development) have not been tested, however. 
3. Once the service is running, copy the URL given to you by Azure (or, if you setup locally, the address from IIS or Kestral, making sure you set up a 1:1 NAT in your firewall and that you have a public IP, and copy-paste that to the [WPF/Console Application](https://github.com/olaafrossi/HueControlExample)

## How to get it running locally

1. Use VS2019 & and the [dotnetcore 3.1 hosting bundle](https://download.visualstudio.microsoft.com/download/pr/9b9f4a6e-aef8-41e0-90db-bae1b0cf4e34/4ab93354cdff8991d91a9f40d022d450/dotnet-hosting-3.1.6-win.exe)
2. Open the solution in VS2019 and select `HueControlWebAssemblyExample.Server` as the startup project. The combobox for running it should default to "Kestral", but it can run in IIS Express if desired. The advantage of Kestral, among others, is that the hosting port remains the same (5000), while IIS Express picks a random port each time you debug the solution. 
3. Refer to the readme of the client app to connect the client to the server [WPF/Console Application](https://github.com/olaafrossi/HueControlExample)

## How to get it running on the Web

1. The simplest way is to generate a new publishing profile with your Microsoft account and create an [Azure App Service](https://azure.microsoft.com/en-us/services/app-service)
2. First, Restore/Update all NuGet packages. Use the GUI for this, `Project -> Manage NuGet Packages -> Install/Restore`
3. Now create your publish profile: Click `Build` and select publish `HueControlWebAssemblyExample.Server`

* Pick the service of your choice

<p align="left">
<img src="https://github.com/olaafrossi/HueControlWebAssemblyExample/blob/master/Imgs/HueServer3.PNG"
  alt="You will need to create a new profile"
</p>

* If Azure, further pick the type of service note: `only tested on Azure App Service (Windows)`

<p align="left">
<img src="https://github.com/olaafrossi/HueControlWebAssemblyExample/blob/master/Imgs/HueServer5.PNG"
  alt="Choose target type"
</p>

Copy and paste URL for use in the [WPF/Console Application](https://github.com/olaafrossi/HueControlExample)

<p align="left">
<img src="https://github.com/olaafrossi/HueControlWebAssemblyExample/blob/master/Imgs/HueServer6.PNG"
  alt="Setup Name, Subscription, Resource Group, and Hosting Plan"
</p>
