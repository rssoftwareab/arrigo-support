# WebSockets and proxies

## Background

The ArrigoLocal depends heavily on [WebSockets](https://datatracker.ietf.org/doc/html/rfc6455) for both getting updated values from controllers and when using ServerSideFunctions. If your firewall doesn't allow WebSocket connections, or if your reverse proxy server doesn't relay the connections, the aforementioned features will not work.

## Firewalls

Since all vendors have their specific ways of enabling WebSockets we recommend that you simply search the interwebs for your model. Example:
`barracuda firewall enable websockets`

## Reverse proxies

The same thing goes for proxies; google your vendor and follow the examples/guides. Example:
`nginx websockets proxy`

Do note that some proxies require you to configure both the `/arrigo/api/graphql/ws` and `/arrigo/api/wamp` endpoints.

### nginx example

Since we (RS Software) use nginx internally we can share our reverse proxy config:

```
location /arrigo/api/graphql/ws {
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  proxy_http_version 1.1;
  proxy_set_header Upgrade "websocket";
  proxy_set_header Connection "Upgrade";
  proxy_pass http://192.168.0.1:80;
}

location /arrigo/api/wamp {
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  proxy_http_version 1.1;
  proxy_set_header Upgrade "websocket";
  proxy_set_header Connection "Upgrade";
  proxy_pass http://192.168.0.1:80;
}

```
