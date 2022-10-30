# Overview
Using [Envoyproxy](https://www.envoyproxy.io) to encapsulate tcp traffic (in this case ssh) into http. Forward http to an envoyproxy in a different networkzone. Then another Envoyproxy terminates http and releases the tcp traffic.

[SSH-Client] --> [Envoy|TCP-to-HTTP] --> [Envoy|Forward HTTP] --> [Envoy|HTTP-to-TCP] --> [SSH-Server]

# Run
```
docker-compose up
```

```
ssh admin@127.0.0.1 -p 3333
```

# References
* https://www.envoyproxy.io/docs/envoy/latest/intro/arch_overview/http/upgrades#tunneling-tcp-over-http


* https://github.com/envoyproxy/envoy/blob/ba81ae537e722ad99906599f5d3ad367ca854433/configs/encapsulate_in_http2_connect.yaml
* https://github.com/envoyproxy/envoy/blob/ba81ae537e722ad99906599f5d3ad367ca854433/configs/terminate_http2_connect.yaml
* https://github.com/envoyproxy/envoy/blob/ba81ae537e722ad99906599f5d3ad367ca854433/configs/proxy_connect.yaml

# Todo
* configure mTLS Tunnel between Proxies 