# Aufgabe 2 - ASP.NET Core Web API

## Aufgabenstellung

Erstelle ein ASP.NET Core Web API Projekt (von Scratch, siehe [dotnet new webapi](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-new-sdk-templates#webapi)) und verändere / erweitere den Code wie folgt:

### Technologien und Struktur

- verwende [.NET 7 oder aktueller](https://dotnet.microsoft.com/en-us/download)
- verwende [Entity Framework Core](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore) mit einem beliebigen [Datenbank Provider](https://learn.microsoft.com/en-us/ef/core/providers/?tabs=dotnet-core-cli)
- entscheide dich für ein [Controller-basiertes oder minimal API](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/apis?view=aspnetcore-7.0)

### Endpunkte

Das Web API soll über Endpunkte mit folgenden Eigenschaften verfügen:

| HTTP request method | route        | request parameters            | description     |
| ------------------- | ------------ | ----------------------------- | --------------- |
| POST                | /pizzas      | a pizza (body)                | create a pizza  |
| GET                 | /pizzas      | -                             | read all pizzas |
| GET                 | /pizzas/{id} | an id (route)                 | read a pizza    |
| PUT                 | /pizzas/{id} | an id (route), a pizza (body) | update a pizza  |
| DELETE              | /pizzas/{id} | an id (route)                 | delete a pizza  |

Alle Endpunkte sollten Content-Type `application/json` verwenden.

### Entitäten

_Pizza_

| field       | type                  | required | comment                                             |
| ----------- | --------------------- | -------- | --------------------------------------------------- |
| id          | int or Guid           | yes      | key / unique identifier, ideally database-generated |
| description | string                | yes      | maximum length of 32 characters                     |
| diameter    | int                   | yes      | 20 <= diameter <= 40                                |
| bakingTime  | double                | no       | 0.0 <= bakingTime                                   |
| toppings    | ICollection<Topping\> | yes      | one to many relation                                |

_Topping_

| field       | type        | required | comment                                             |
| ----------- | ----------- | -------- | --------------------------------------------------- |
| id          | int or Guid | yes      | key / unique identifier, ideally database-generated |
| description | string      | yes      | maximum length of 32 characters                     |

### Abgrenzung Aufgabenstellung

Um Umfang und Komplexität zu reduzieren sind folgende Aspekte NICHT Teil der Aufgabenstellung:

- Sicherheit - insbesondere Authentifizierung / Autorisierung oder Verwendung von TLS / HTTPS
- [Verwendung von Datentransferobjekten](https://learn.microsoft.com/de-de/aspnet/web-api/overview/data/using-web-api-with-entity-framework/part-5)
- Logging
- API Versionierung

## Bewertungskriterien

Wir achten bei der Bewertung deiner Resultate unter anderem auf:

- Anwendung von Entwurfsmustern / Design Patterns und Best Practices
  - z.B. [Clean Code](https://gist.github.com/wojteklu/73c6914cc446146b8b533c0988cf8d29), [C# Coding Conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions) oder [SOLID Prinzipien](https://en.wikipedia.org/wiki/SOLID)
- Einsatz von Packages
- Lauffähigkeit
- Verwendung von HTTP Status Codes
