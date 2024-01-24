```yaml
version: v2beta1  
name: affiliate-svc  
  
pipelines:  
  dev:  
    run: |-  
      start_dev app  
# This is a list of `dev` containers that are based on the containers created by your deployments  
dev:  
  app:  
    # Search for the container that runs this image  
    imageSelector: registry-gitlab.firegroup.io/onetracking/affiliate-service  
    logs:  
      lastLines: 100  
    restartHelper:  
      inject: true  
    # Replace the container image with this dev-optimized image (allows to skip image building during development)  
    devImage: ghcr.io/loft-sh/devspace-containers/alpine:3  
    # Sync files between the local filesystem and the development container  
    command:  
      - ./server  
    sync:  
      - path: ./bin/server.zip  
        file: true  
        initialSync: mirrorLocal  
        disableDownload: true  
        waitInitialSync: false  
        onUpload:  
          restartContainer: true  
          exec:  
            - command: |-  
                unzip ./bin/server.zip bin/server -d ./  
                chmod +x ./bin/server  
                mv ./bin/server ./server
```

Ta có thể nén file để upload nhanh hơn:

```bash
GOOS=linux CGO_ENABLED=0 go build -ldflags="-s -w" -o ./bin/server ./cmd/server/...
zip bin/server.zip bin/server
```