`simplehttp2server` serves the current directory on an HTTP/2.0 capable server.
This server is for development purposes only.

# Push Manifest

`simplehttp2server` supports the [push manifest](https://www.npmjs.com/package/http2-push-manifest).
All requests will be looked up in a file named `push.json`. If there is a key
for the request path, all resources under that key will be pushed.

Example `push.json`:

```JS
{
  "index.html": {
    "/css/app.css": {
      "type": "style",
      "weight": 1
    },
    // ...
  },
  "page.html": {
    "/css/page.css": {
      "type": "style",
      "weight": 1
    },
    // ...
  }
}
```

Support for weighting those pushes is not yet implemented.

# TLS Certificate

Since HTTP/2 requires TLS, `simplehttp2server` checks if `cert.pem` and
`key.pem` are present. If not, a self-signed certificate will be generated.

# Download

`simplehttp2server` is `go get`-able:

```
$ go get github.com/GoogleChrome/simplehttp2server
```

Precompiled binaries can be found in the [release section](https://github.com/GoogleChrome/simplehttp2server/releases).

# License

Apache 2.

# COMMANDLINE INSTALL FOR MAC
```
curl -o ${HOME}/.http2/simplehttp2server https://github.com/GoogleChrome/simplehttp2server/releases/download/2.0.0/simplehttp2server_darwin_amd64
chmod 755 ${HOME}/.http2/simplehttp2server
echo alias http2='~/.http2/simplehttp2server' >> ${HOME}/.bash_profile
```

* Goto your wwwroot directory and run `http2` site will be hosted on [https://localhost:5000](https://localhost:5000) (automatic selfsigned TLS certificate will be created if not found in the directory) 

