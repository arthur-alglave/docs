---
title: "Runtime Engine"
category: "Mendix Runtime"
menu_order: 10
description: "A detailed description of the functions and structure of the Mendix Runtime Engine/Runtime"
tags: ["runtime", "load balancer", "container", "engine", "instance"]
---

## 1 Introduction

The Mendix Runtime Engine executes the application model that is created in Studio or Studio Pro. It serves pages to the [Runtime Client](runtime-client), executes microflows, calls web services, generates documents, communicates with the database, and much more.

### 2.1 Runtime Engine Architecture

The Mendix Runtime Engine architecture consists of multiple components to execute logic, manage data, communicate with the client, and implement security. The diagram below presents an overview of all of the components, which is followed by a short description of their responsibilities:

{{% image_container width="600" %}}
![Runtime Engine](attachments/runtime/runtime-engine.png)
{{% /image_container %}}

The Mendix Runtime Engine consists of the following components:

* **Platform core** – responsible for the correct startup and shutdown of your application and loading the required libraries and extensions
* **Object cache** – handles the creation and removal of objects
* **Session manager** – manages the creation of user sessions and the cleanup of logged-out or abandoned sessions.
* **HTTP server** – included in the Mendix Runtime to handle requests from the web and mobile client and to handle service requests
* **Microflow engine** – executes your microflows and microflow activities
* **Data layer** – persists and retrieves objects from your application database; also responsible for creating and updating the database structures required to persist your data: the data layer supports a large number of different databases, and data is stored using common data model design best practices (for details, see the section [What Databases Does Mendix Support?](../app-capabilities/data-storage#database-support) in *Data Storage*)
* **Integration layer** – handles incoming and outgoing service requests for web services, REST APIs, app services, and OData
* **Client API** – responsible for communication with web and mobile clients; the API is used to retrieve data, persist data changes, and execute microflow logic
* **Configuration API** – this JSON API is used by the Developer Portal and container buildpack to configure the runtime
* **Monitoring API** – this JSON API is used by the Developer Portal and container buildpack to retrieve monitoring metrics
* **Custom APIs** – this Java APIs is used to extend the Mendix Runtime (for example, with microflow activities or entity listeners)
