---
title: "Getting started with SDKs"
excerpt: ""
---
## Overview
This topic explains the prerequisites you must consider when you're setting up a LaunchDarkly SDK for the first time.
## Prerequisites
Regardless of which SDK you use, everyone who integrates LaunchDarkly with their code must consider the following prerequisites. Making decisions about the items listed below will help you use feature flags in a way that makes sense for your use case, customers, security considerations, and existing network architecture.

Consider the following factors when you're starting to integrate LaunchDarkly SDKs with your code:

1. **Determine what kind of SDK you need to use.** 
 Depending on your use case, you may need a server-side, client-side, or mobile SDK. 
 You only need one SDK per application or service. You can use multiple SDKs if your product is comprised of applications or services written in multiple languages. 
 You do not need multiple SDKs to support frontend and backend behavior, but we support this configuration if it works best for you.
 To learn more about SDKs, read [Client-side and server-side SDKs](./client-side-and-server-side).
2. **Identify the language you wish to use**. In some cases, we support multiple SDKs for a language. To learn more, read [Supported SDKs](#supported-sdks).
3. **Confirm that your tech stack's versions are compatible with the SDK you wish to use**. More information about SDK versioning is available in the documentation for a specific SDK, or in the SDK's readme in Github.
4. (Optional) **Determine if you need to use the LaunchDarkly relay proxy.** 
 To learn more, read [The LaunchDarkly relay proxy](./the-relay-proxy).

## Implementation guidelines for LaunchDarkly SDKs
Here are some basic guidelines for implementing LaunchDarkly SDKs:

### Consider your SDK use case
The SDK types have different security considerations as well as some behavioral and architectural differences. They handle flag evaluations differently, utilize different kinds of SDK keys, and support different languages.

To learn more, read [Client-side and server-side SDKs](./client-side-and-server-side).

### Plan for a large initial payload from the streaming endpoint
The initial payload contains all the targeting rules for the environment associated with the provided SDK key. If you target a large number of individual users, have a very large number of flags, or have large numbers of extremely complicated rules, then this can increase the initial payload size. Configure any relevant timeout options to anticipate a large initial load. This helps prevent the SDK from timing out.

### Ensure you have a reliable network connection for first-time initialization
The SDK will time out if it cannot get a network connection to LaunchDarkly. Failure to connect is a recoverable error, so the SDK will keep trying to reconnect, but a timeout could happen in the middle of an attempt. If the SDK times out during a first-time initialization, it will serve the flag values you defined in your application code until it can connect to LaunchDarkly.

### Implement SDKs in a singleton pattern
Your SDK should only initialize once statically, and that instance should be the exclusive instance you use. When you create multiple SDK instances, previous instances may leak into memory and stay active long after the context they were created in is destroyed. 

When you have enough of these instances running, they can cause bottlenecks in the connection to the streaming endpoint.

## <a name="supported-sdks"></a>Supported SDKs
We provide the following SDKs:

Server-side SDKs:

* [.NET](./dotnet-sdk-reference)
* [C/C++ (server-side)](./c-server-sdk-reference)
* [Go](./go-sdk-reference)
* [Haskell](./haskell-server-sdk-reference) 
* [Java](./java-sdk-reference)
* [Node.js (server-side)](./node-sdk-reference)
* [PHP](./php-sdk-reference)
* [Python](./python-sdk-reference)
* [Ruby](./ruby-sdk-reference)

Client-side SDKs:

* [Android](./android-sdk-reference)
* [C/C++ (client-side)](./c-sdk-reference)
* [Electron](./electron-sdk-reference)
* [iOS (Objective-C)](./ios-objc-sdk-reference)
* [iOS (Swift)](./ios-sdk-reference)
* [JavaScript](./js-sdk-reference)
* [Node.js (client-side)](./node-client-sdk-reference)
* [React](./react-sdk-reference)
* [React Native](./react-native-sdk-reference)
* [Roku](./roku-sdk-reference) 
* [Xamarin](./xamarin-sdk-reference)