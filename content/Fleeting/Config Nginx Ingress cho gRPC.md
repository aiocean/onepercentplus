Sử dụng config này cho gRPC

```yaml
static_resources:  
  listeners:  
    - name: listener_grpc  
      address:  
        socket_address: { address: 0.0.0.0, port_value: 8080 }  
      filter_chains:  
        - filters:  
            - name: envoy.filters.network.http_connection_manager  
              typed_config:  
                "@type": type.googleapis.com/envoy.extensions.filters.network.http_connection_manager.v3.HttpConnectionManager  
                access_log:  
                  - name: envoy.access_loggers.stdout  
                    typed_config:  
                      "@type": type.googleapis.com/envoy.extensions.access_loggers.stream.v3.StdoutAccessLog  
                codec_type: auto  
                stat_prefix: ingress_http  
                route_config:  
                  name: local_route  
                  virtual_hosts:  
                    - name: local_service  
                      domains: [ "*" ]  
                      routes:  
                        - match:  
                            prefix: "/onetracking.v1.ApplicationService/"  
                          route:  
                            cluster: onetracking_v1_ApplicationService  
                        - match:  
                            prefix: "/onetracking.v1.CampaignService/"  
                          route:  
                            cluster: onetracking_v1_CampaignService  
                http_filters:  
                  - name: envoy.filters.http.router  
                    typed_config:  
                      "@type": type.googleapis.com/envoy.extensions.filters.http.router.v3.Router  
  clusters:  
    - name: onetracking_v1_CampaignService  
      connect_timeout: 5s  
      type: strict_dns  
      http2_protocol_options: {}  
      lb_policy: round_robin  
      load_assignment:  
        cluster_name: onetracking_v1_CampaignService  
        endpoints:  
          - lb_endpoints:  
              - endpoint:  
                  address:  
                    socket_address:  
                      address: firegrowth-svc-ot-campaign-VAR_ENV-firegroup  
                      port_value: 443 # internal port  
    - name: onetracking_v1_ApplicationService  
      connect_timeout: 5s  
      type: strict_dns  
      http2_protocol_options: {}  
      lb_policy: round_robin  
      load_assignment:  
        cluster_name: onetracking_v1_ApplicationService  
        endpoints:  
          - lb_endpoints:  
              - endpoint:  
                  address:  
                    socket_address:  
                      address: firegrowth-svc-ot-application-VAR_ENV-firegroup  
                      port_value: 443 # Internal port
```

^680908

Nếu ở trong trường hợp bị Nginx bọc ở phía trước thì phải config để nginx passby grpc ([[Config Nginx Ingress hỗ trợ envoy gprc phía dưới]])