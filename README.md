# xray-configuration

This repository contains the optimal configurations for Xray and the Remnawave panel, providing you with a starting point for deploying various protocols securely and effectively.

## How to Implement These Configurations in Remnawave

In Remnawave, these configurations should be used to create **Config Profiles**. To use a configuration:
1. Navigate to the **Config Profiles** section in your Remnawave panel.
2. Create a new profile or edit an existing one.
3. Paste the contents of the desired `.json` file from this repository into the configuration editor.
4. **Important**: Remember to replace any placeholder values (like `USE OWN VALUE!`, `private key`, `/path/to/cert.crt`) with your actual environment variables or generated keys before saving.
5. Apply the profile to your nodes and assign users to the appropriate internal squads.

## Configurations Included

### 1. Advanced Load Balancer (`advanced-balancer.json`)
Demonstrates how to group multiple outbound connections into a load balancer using the Remnawave `injectHosts` directive and monitor health using `burstObservatory`.
**Usage:** Use this when you have multiple upstream servers and want the panel to automatically inject them into your routing strategy based on latency.

### 2. Server Routing Bridge (`server-routing-bridge.json`)
The Bridge Profile acts as the destination server in a multi-server routing setup.
**Usage:** Deploy this profile on the target/backend server (e.g., DE-001) that will receive traffic forwarded from your entry server.

### 3. Server Routing Public (`server-routing-public.json`)
The Public Profile acts as the entry node. It routes traffic based on rules (e.g., direct for specific regions) and sends all other traffic over a Shadowsocks outbound to the bridge node.
**Usage:** Deploy this on the server users connect to directly (e.g., RU-001).
**Note:** You must replace `ADDRESS OF DE-001`, `ПАРОЛЬ С ПРОШЛОГО ШАГА`, `USE OWN VALUE!`, `USE OWN KEY!`, and `REPLACE WITH OWN VALUES!` with your actual values before deploying this configuration.

### 4. VLESS TCP REALITY (`vless-tcp-reality.json`)
The optimal VLESS TCP REALITY configuration, incorporating specific routing and blocking rules.
**Usage:** A robust, standard configuration utilizing REALITY to disguise traffic as connections to an allowed site (e.g., github.com). Excellent for bypassing deep packet inspection.

### 5. VLESS gRPC REALITY (`vless-grpc-reality.json`)
The optimal VLESS gRPC REALITY configuration, maintaining standard routing and blocking rules.
**Usage:** Uses gRPC multiplexing. Suitable for situations where TCP traffic might be throttled or when placing Xray behind a proxy/CDN that supports gRPC.

### 6. VLESS XHTTP REALITY (`vless-xhttp-reality.json`)
The optimal VLESS XHTTP REALITY configuration.
**Usage:** Utilizes the experimental xhttp transport for advanced obfuscation techniques.

### 7. VLESS WebSocket TLS (`vless-ws-tls.json`)
The optimal VLESS WebSocket configuration utilizing standard TLS.
**Usage:** The classic choice for putting Xray behind a Content Delivery Network (CDN) like Cloudflare. The `wsSettings.path` should be customized for your setup.

### 8. Trojan WebSocket TLS (`trojan-ws-tls.json`)
The optimal Trojan WebSocket TLS configuration.
**Usage:** Similar to VLESS WS, this is ideal for passing traffic through a CDN, utilizing the Trojan protocol. Ensure you point the certificates to valid paths on your server.

### 9. Hysteria 2.0 (`hysteria2.json`)
The optimal Hysteria 2.0 configuration, maintaining the standard routing and blocking rules.
**Usage:** A UDP-based protocol designed to be highly resilient against network packet loss and throttling. Provides excellent speeds on poor networks. Requires valid TLS certificates.

---
References:
- [Remnawave Documentation - Xray JSON Advanced](https://docs.rw/docs/learn/xray-json-advanced/)
- [Remnawave Documentation - Server Routing](https://docs.rw/docs/learn/server-routing)
