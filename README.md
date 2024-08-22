# Shuneo is learning Cloud Computing

# connect a route A to route B

set route ip adress and submask

```bash
route(config)# interface [gate]
route(config-if)# ip address [ip] [submask]
```
set route from routeA to routeB
```bash
routeA(config)# ip route 0.0.0.0 0.0.0.0 [ipRouteB]
```

ping from routeA to routeB
```bash
routeA(config)# ping [ipRouteB]
```

ping to server
```bash
routeA(config)# ping [ipServer]
```
