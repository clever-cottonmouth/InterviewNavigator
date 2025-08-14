## **File**Upload Limits in .NET

**maxRequestLength (ASP.NET)**

* **Location:** `web.config`
* **Purpose:** Specifies the maximum size (in KB) of the request, which includes file uploads.
* **Default:** 4096 KB (4 MB)

```xml
<system.web>
  <httpRuntime maxRequestLength="102400" /> <!-- 100 MB -->
</system.web>
```


ASP.NET Core – `RequestSizeLimit`

[RequestSizeLimit(50_000_000)] // 50 MB
public IActionResult Upload(IFormFile file) { ... }
