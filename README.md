**Please support us by giving a Star/Fork :star: . You'll receive updates - we still have much code to do ☕**

### AppFullStackDemo .NetCore 3.1 DDD/SOLID/CQRS/Api Rest - CleanCode
### Angular Material Panel + React Native Mobile.


* Note: Esse documento também está disponível em Português. Por favor veja o README-PT.
* Note 2: I've also recorded some Vídeos tutorials that shows how to RUN this app. Just access my channel: https://www.youtube.com/channel/UCFzZD9snKFKZAx-FwL6SpeQ
* Note 3: You can use just parts of this project. Example: If you are not MobileDev, just ignore it.

# 
### Business Logic:
How it works: WebPanel (Angular Material) and MobileApp (React Native) will have a Login-Screen, that will works with the
BackEnd to Login - in case of Panel it will provide full-management for DashBoard + 3 CRUDS + List/Details screen. In the
case of MobileApp you will be allowed to see details of Device, and register it on portal. Once registered, you'll see it
on Panel linked to the logged-user (details of Device) and will interact to the Dashboard.

**FrontEnd** Will have a LoginScreen, where user can click on "Register new user" and create a new user, or also login
with an existing. Panel you will have a DashBoard (showing graphics with Number of Devices per AndroidVersion, and 
number of devices per Manufacturer). Users logged on Panel will be allowed to create another Users that can also Login
into Panel and MobileApp. So the Users Screen will comes with a "CRUD" function to List, Create, Edit and Delete Users.

On UserScreen (List) will be a button to LIST all the Devices for that user (Device Details Screen). So when you Login in
a Mobile Device, user can Register the Device, it will be available with Details on Panel. There will plus 2 screens to
manage Manufacturer and DeviceModel. Once a Equipment belongs to a DeviceModel > A DeviceModel to a Manufacturer:

Manufacturer: Samsung. DeviceModels: Galaxy S8, Galaxy S9, Galaxy S10, Galaxy Note 8, Galaxy Note 9.
Manufacturer: Xiaomi. Device Models: Mi8, Mi9, Mi10, Redmi8, Redmi 9, Mi Max 2, Mix Max3, Mi Mix2.

BackEnd will automatically handle it, looking for the Model and Manufacturer, and creating it IF does not exists, or
attach the new Equipment to an existing Manufacturer>Model. Angular Panel is also ready to work with the Token, with an
Interceptor Layer to Deal with 401/403 codes, show good messages, alerts, ballon messages, modals and a lot of cool
things with a nice Material-Interface.

**BackEnd** will provide an API to support Mobile/Panel apps. All the "Brain" of the App: The Business Logic, Entities,
the Database layers, API, Services/Handlers, will be here. **Under the hood**: The BackEnd .NET Core with Rich 
Architecture DDD/SOLID with CleanCode will be running providing all this data for both apps.

**MobileApp** can "register" the Device on backend - informing to backend the Manufacturer, Model, Phone Number, Serial
Number, IMEI and some other information. You could use your Real Device or also an Emulator (like Android Studio or
Genymotion) to test it. Once it's React Native and you have a Mac - you can work on it to compile it for iOS.

Note that MobileApp is a "bônus": This App will basically just list some information about the Device, and allow this
device to be registered on the backend, that will appears on the Panel. I'm not a React Native developer, so you can
help-me to increase this App and make it better :)

![Login Panel](https://github.com/fernandopassaia/app_fullstackdemo/blob/master/panel/Panel1.png)

![Register Page](https://github.com/fernandopassaia/app_fullstackdemo/blob/master/panel/Panel2.png)

![DashBoard](https://github.com/fernandopassaia/app_fullstackdemo/blob/master/panel/Panel3.png)

![DashBoard2](https://github.com/fernandopassaia/app_fullstackdemo/blob/master/panel/Panel4.png)

![UpdateDeviceModel](https://github.com/fernandopassaia/app_fullstackdemo/blob/master/panel/Panel5.png)

![UserCrud](https://github.com/fernandopassaia/app_fullstackdemo/blob/master/panel/Panel6.png)

![UserDetails](https://github.com/fernandopassaia/app_fullstackdemo/blob/master/panel/Panel7.png)

![DeviceDetails](https://github.com/fernandopassaia/app_fullstackdemo/blob/master/panel/Panel8.png)

# 
### BackEnd .NET Core 3.1 C# + EF Core (SQLServer). Rich Architecture DDD/SOLID CleanCode using:
* Rich Modeling (Models-Entities, Enums, ValueObjects) (read below for the Business Logic)
* Api REST + Handlers (Services) to Deal with the Requests + Dependency Injection
* JWT Token to Auth Parts + Claims + JSON to Data
* Handler Layer (you can also call it as "Service") to "orchestrate" the requests
* Entity Framework Core with separated Layers for the ConfigMap of Tables + SQL Server Express (Free)
* Repositories Layer + Unit of Work + 3 CRUDS (EF Code First)
* CQRS to Receive Queries and Comands and Return Results
* Validation by Contracts on Commands (Fail-Fast Validations)
* Pattern (BaseCommandResult) for the Returns of the API on a Well-defined type
* Shared Project (classlib) for Field Formaters, Validations, Cryptografy
* Mock-DataCreator to fill start-database with some test-data
* Unit-Tests for Commands, Queries, Repositories, Entities and Handlers
* Note: DataBase can be Easily replaced (to Postgres, MySQL) once layers are very well separated.

### FrontEnd Angular + Material Panel + Login + Auth + 3 Full-CRUDS + Detail screen:
* Complete Panel to Create Account, Login + DashBoard + 3 Entire CRUDS (read below for the Business Logic)
* Nice Interface using Angular Material, Modals, MatTable, Chartlist and more.
* CQRS Models and Interfaces based on BackEnd (Commands and Results)
* Layer for the Services and API Communication - Capable to Catch Results and Display Messages (like
  good result or list of validation-errors) coming from the backend (you'll not need to catch on each
  service or screen the messages to display to user what happens) (httpinterceptor)
* Separated Modules and Rotes Files for better Organization.
* Shared Services for Dialogs, Notification Messages, Modal Screens, Enum Description.
* Auth Guard / Auth Interceptor to Deal Perfectly with the Tokens, Authentication, Headers (401/403).

### Mobile React-Native + Device-Info:
Login Screen that Will Communicate with the BackEnd for Auth and Store the JWT. Once Logged, MobileApp will
allow user to add this device to the account with the Details of the Device (Imei, PhoneNumber, Serial,
manufacturer, model). Once Registered, Device and it's info will appears on the Panel > User > Equipment list.

# 
### License and USE of this App in a RealWorld Scenario:
Note: This App is FREE and FULL OpenSource. You can Use it as a base for your system, or you can also colaborate with me
to improve it. In a REAL-WORLD, this App needs to be better planned:

Users should belong to a Company (or even better - User should belong to a Real-Entity like Employee or something),
Claims should have Profiles (like Master, Admin...) where the Claims will be connected (not right to the user). We also
need a screen to manage the CRUD of the Claims (that we don't have on this app). Create category for the Devices:

We also need to implement things like RefreshToken Logic, WelcomeEmail, Recover Password, Change PassWord Screen and go
on and on - lot of other things to use this app in a Real-scenario. We need to adapt lot of things to a REAL-WORLD
Scenario of Real-Business needs Logic.

But for now: Remember that this app is a "demo" of Programming, Architecture and Techinical Skills - NOT a demo of
Real-World App. So we will keep the business-stuff simple to Focus on Technical stuff. Anyway, you can use it as a base
of a Architecture, and start your own system under it, following the patterns already implemented on it. You can use it
as a "skeleton" for your next Real-Software. Good luck :cake:

# 
### How to RUN it (manually way):
There are two ways to run this app: Manually (below) or by Docker with docker-compose (please read on the end of this Readme).

You can Develop and Run it on Windows, Linux and MacOs. In My Machine: I've Used Linux Ubuntu 20.04 and VS Code :)

**Tutorial**: If you prefer Video Tutorial about how to run this app, please access here:
https://www.youtube.com/watch?v=8z7R0NsU5tw

If you want to know how do i configure my Linux Envoirnment: VSCode, extensions, the fonts i use, the system variables
of my envoirnment and how to i configure then, the packages i use: I have it in a documented way. Please take a look
to my repo called **docsamples > generaldocs**. You'll see files and folders for .Net Core, VsCode, Angular, React 
Native - this are my references and the things i use to work in these languages.

I also use "Insomnia" to TEST API, but you can use Postman or if you prefer, install some integrated tool like Swagger.
I also use "Azure Data Studio" to check the DataBase in case of need. Note: I've also tested all this APP and Envoirment
using Windows 10 and it also works perfect, also in VS Community 2019. Basically chooose your favorite :trollface:

### How to Run the BackEnd:
SQLServer Connection string for the BackEnd is on "BackEnd>AppFullStackDemo.Api>appsettins.json", so please set-up your
SQL Connection Server info before try to RUN the APP. If the connectionstring does not exists on this file, EF will use
the Default string on "AppFullStackDemoContext.cs".

After configure your connection, entre on the main folder (BackEnd) and run:
<li>dotnet restore</li>
<li>dotnet build</li>

After that, enter on ".Infra" and Run the Command:
<li>dotnet ef --startup-project ../AppFullStackDemo.Api/ database update</li>
<br />
**Creating FakeMockData**:
You can start your app with some FakeMockData like a User, some Manufacturers, Devices, then you can see how it works,
login into panel. To do it you just need to run a TEST: Open the "BackEnd > AppFullStackDemo.Tests > MockDataCreator > 
FakeDataCreator" and run the test. IMPORTANT: You have to run the migration and create the DB first.

The MockDataCreator will generate the First LOGIN, that you can use on Panel/Mobile to Login. Then login with:
<li>Login: admin</li>
<li>Password: admin</li>

Then, on the ".Api" folder run the command: 
<li>dotnet run</li>

The Api should start. If you see it running on PORT 4001, well done. BackEnd is ready to go.

### How to Run the FrontEnd:
To Run the Angular AND the Mobile, first of all you need to install NodeJs and NPM. In my personal machine, I'm using
Node 14.2.0 and NPM 6.14.4. Then, Inside the FrontEnd folder run:

<li>npm install</li>
<li>ng serve --o</li>

### How to Run the Mobile:
Inside Mobile folder go to "src > services > api.js". You'll need to setup your IP connection (replace 192.168.1.10).
To discover your IP use "ifconfig" (linux) or "ipconfig" (windows). Note: I've tried to use "localhost" with React-Native
api, but it conflicts. So I've used the Machine-IP instead.

You need to create a file called "local.properties" inside "android" Folder with your SDK Location. In my case:
sdk.dir = /home/fernandopassaia/Android/Sdk

Then inside Mobile folder:
<li>npm install</li>
<li>react-native run-android</li>

(Note: you'll need to setup your envoirnment and have a Device or Emulator running)

### Tutorial vídeos on Youtube:
I've recorded some videos also showing you how to Run this App. Just go to these channel:
<li>https://www.youtube.com/channel/UCFzZD9snKFKZAx-FwL6SpeQ</li>

# 
###  How to RUN it (with docker-compose):

# 
### Additional Info:
**Note about the CLAIMS**: System comes with a Claim Table and have 5 base claims: dashboard, manufacturer, devicemodel,
user and equipment. The "better" way to implement it should be granulated (user.list, user.create, user.edit) and
the system needs a Screen to Edit the Claims, and a way to "link" the User to the Claims. In my personal opinion
system should have "Profiles" (like Master, Admin, Users...) and user will receive claims based on a Profile.

Anyway, as we describe, this system is not a Sample of Business rules. You should improve it according to your needs.
So basically when a User is created, on the "UserHandler" the claims (all of them) will be gave to the User, and it
will have all accesses. Anyway, if you want to test a "forbidden" and Angular Interceptor, you can delete it from
"UserClaim" table (that links Claims to the Users). Than just logout (to delete token) and go on...

**Note about the Template**: I've used a Ready-Template from internet. So basically most of the things, html/css code
comes from it. Part of items i've done (like modals, messages, some designs), installed and configured components.
The Template comes with no code to integrate to backend, no services, no interceptor, auth, nothing at all. Just
clean Design-Material template. I'm not a Designer, so i have to use a ready-to-go template to go-ahead with Panel.

**Please support us by giving a Star/Fork :star: . You'll receive updates - we still have much code to do ☕**

