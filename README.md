# HTTPServer

## How 2 use

```cpp
#include "httpserver.h"

class IndexHandler : public HTTPRequestHandler
{
public:
    void operator()(const HTTPRequest& request, HTTPResponse& response)
    {
        response.Header("Content-Type", "text/html; charset=UTF-8");
        response.Data("hello world");
    }
};

int main()
{
    HTTPServer server;
    server.Init();
    
    server.AddHandler<IndexHandler>("/");
    
    server.AddMIME("css", "text/css");
    server.AddMIME("ico", "image/x-icon");
    server.AddMIME("png", "image/png");
    
    server.Run();
    
    server.Cleanup();
    return 0;
}
```
