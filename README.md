# Container Security

Demonstrates the security impact of Docker best practices by comparing a vulnerable container against a hardened one.

## Comparison

| | Bad Image | Good Image |
|---|-----------|------------|
| Base | ubuntu:latest (845MB) | python:3.12-slim (209MB) |
| User | root | appuser (non-root) |
| Extra tools | curl, wget | none |
| Pinned deps | no | yes |
| Trivy vulns | 631 | 2 |

## Key Practices

- Use slim/minimal base images
- Run as non-root user
- Pin dependency versions
- Remove unnecessary tools
- Use multi-stage builds
- Scan images with Trivy before deploying

## Usage

Build and scan both images:
```
docker build -f Dockerfile.bad -t bad-app .
docker build -f Dockerfile.good -t good-app .
trivy image bad-app
trivy image good-app
```

