# xray-configuration

This repository contains the best configurations for Xray and the Remnawave panel based on the official documentation.

## Configurations Included

### 1. `advanced-balancer.json`
This file contains the configuration for a load balancer setup using the Remnawave `injectHosts` directive.
It demonstrates how to group multiple outbound connections into a load balancer and use the `burstObservatory` to monitor their health.

References:
- [Remnawave Documentation - Xray JSON Advanced](https://docs.rw/docs/learn/xray-json-advanced/)

### 2. `server-routing-bridge.json`
This file contains the Bridge Profile for server routing. It acts as the destination server in a multi-server setup (e.g., DE-001).
It defines an inbound configuration that listens for connections coming from another node.

References:
- [Remnawave Documentation - Server Routing](https://docs.rw/docs/learn/server-routing)

### 3. `server-routing-public.json`
This file contains the Public Profile for server routing. It acts as the entry node (e.g., RU-001).
It routes traffic based on rules (e.g., direct for specific regions) and sends all other traffic over a Shadowsocks outbound to the bridge node (e.g., DE-001).
**Note:** You must replace `ADDRESS OF DE-001`, `ПАРОЛЬ С ПРОШЛОГО ШАГА`, `USE OWN VALUE!`, `USE OWN KEY!`, and `REPLACE WITH OWN VALUES!` with your actual values before deploying this configuration.

References:
- [Remnawave Documentation - Server Routing](https://docs.rw/docs/learn/server-routing)

### 4. `vless-tcp-reality.json`
This file contains the optimal VLESS TCP REALITY configuration, incorporating specific routing and blocking rules.

### 5. `vless-grpc-reality.json`
This file contains the optimal VLESS gRPC REALITY configuration, maintaining standard routing and blocking rules.

### 6. `vless-xhttp-reality.json`
This file contains the optimal VLESS XHTTP REALITY configuration, providing robust connection obfuscation with standard routing rules.

### 7. `trojan-ws-tls.json`
This file contains the optimal Trojan WebSocket TLS configuration, maintaining standard routing and blocking rules.
