# Containerize_Trivy_SARIF

This repository demonstrates containerization and automated vulnerability scanning using Trivy with SARIF output for DevSecOps workflows.

## Features
- **Dockerized FastAPI Application**: Simple FastAPI app containerized for local development and testing.
- **Trivy GitHub Action**: Automated scanning of filesystem, dependencies, and configuration for vulnerabilities, misconfigurations, and secrets.
- **SARIF Reporting**: Vulnerability results are output in SARIF format for integration with GitHub security features.
- **Fail on Severity**: CI workflow fails if vulnerabilities of MEDIUM, HIGH, or CRITICAL severity are found.

## Usage

### Build and Run Locally
```powershell
# Build the Docker image
docker build -t trivy-sarif:local .

# Run the container (exposes FastAPI on port 8000)
docker run -p 8000:8000 trivy-sarif:local
```

### GitHub Actions Workflow
- On every push or pull request, Trivy scans the repository for vulnerabilities and misconfigurations.
- The workflow fails if any MEDIUM, HIGH, or CRITICAL vulnerabilities are detected.
- SARIF results are uploaded for review in GitHub Security tab.

### Trivy Scan Details
- Scans OS packages, application dependencies, configuration files, and secrets.
- Uses Trivy's latest GitHub Action for best compatibility.
- Only vulnerabilities of MEDIUM, HIGH, or CRITICAL severity will fail the workflow.

## Files
- `Dockerfile`: Containerizes the FastAPI app.
- `src/app.py`: FastAPI application entrypoint.
- `requirements.txt`: Python dependencies.
- `.github/workflows/trivy.yml`: CI workflow for Trivy scanning and SARIF upload.

## References
- [Trivy Documentation](https://aquasecurity.github.io/trivy/)
- [GitHub Actions](https://docs.github.com/en/actions)
- [SARIF Format](https://docs.oasis-open.org/sarif/sarif/v2.1.0/sarif-v2.1.0.html)
