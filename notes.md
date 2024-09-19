## .NET

- in `API.csproj` -> `<Nullable>enable</Nullable>` will help notify us if we're using something that might be null, and will enable warnings in our entitiesl
- `required` flag will force the constructor usage to provide something, and will not accept an empty string
- when installing stuff, match the major version to the major version of .NET we're using (8.0.8 for this project)

```C#
public class DataContext(DbContextOptions options) : DbContext(options)
{
}
```

is equivalent to

```C#
public class DataContext : DbContext
{
    public DataContext(DbContextOptions options) : base(options)
    {
    }
}
```

- `appsettings.json` is always read, `appsettings.Development.json` is only read in dev mode
- probably don't use SQLite for production, but for Dev it's great cuz it just WORKS. Entity Framework also makes it easy to switch to something else

### Entity Framework

- ORM = Object Relational Mapper
- Features
  - Querying
  - Change tracking
  - Saving
  - Concurrency
  - Transactions
  - Caching
  - Built-in conventions (e.g. `Id` has to be spelled like that)
  - Configurations - can override conventions
  - Migrations - gives us the ability to create a DB schema and automatically create our DB (this is called "code first")
- We specifically want `Microsoft.EntityFrameworkCore.Sqlite`, NOT `Microsoft.EntityFrameworkCore.Sqlite.Core` or anything else
- by convention, EntityFramework will use "Id" as the primary key and will autoincrement
- `dotnet ef migrations add InitialCreate -o Data/Migration`
- `dotnet ef database update`

### Angular

- http requests always\* complete, so we don't have to manually unsubscribe
