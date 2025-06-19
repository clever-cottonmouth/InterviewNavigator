Microsoft.AspNetCore.Authentication.JwtBearer

Microsoft.AspNetCore.Identity.EntityFrameworkCore

Microsoft.IdentityModel.Tokens

System.IdentityModel.Tokens.Jwt

Microsoft.EntityFrameworkCore.SqlServer

Microsoft.EntityFrameworkCore.Tools

Automapper

Serilog
Serilog.AspNetCore
Serilog.Sinks.Console

Serilog
Serilog.AspNetCore
Serilog.Sinks.File

Microsoft.AspNetCore.Mvc.Versioning

Microsoft.AspNetCore.Mvc.Versioning.ApiExplorer

---

"ConnectionStrings": {
  "DefaultConnection": "Server=.;Database=Mango_ShoppingCart;Trusted_Connection=true;TrustServerCertificate=true"
},

builder.Services.AddDbContext`<NZWalksDbContext>`(options =>    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));

Add-Migration "Initial"
Update-Databasek
