# CI/CD Practice Application

This is a Spring Boot application configured with GitHub Actions CI/CD pipelines for practice purposes.

## CI/CD Setup

### Branches
- **main**: Production branch
- **develop**: Development branch
- **feature/***: Feature branches (create as needed)

### CI Pipeline
- **Trigger**: Pull requests to `main` or `develop` branches
- **Actions**:
  - Checkout code
  - Set up Java 25
  - Run Maven tests
  - Build project
  - Upload build artifact

### CD Pipeline
- **Trigger**: Push to `main` or `develop` branches
- **Actions**:
  - Checkout code
  - Set up Java 25
  - Build project
  - Validate build artifact
  - Simulated deployment (pre-check, deploy, post-check)
  - Uses GitHub secrets: `API_KEY` and `APP_CONFIG`

## Required GitHub Secrets

Before the CD pipeline can run successfully, you need to set up the following secrets:

1. Go to: https://github.com/yasiraraphatdu-byte/aaa/settings/secrets/actions
2. Click "New repository secret"
3. Add:
   - **Name**: `API_KEY`
   - **Value**: `dummy_api_key_for_ci_cd_practice`
4. Add:
   - **Name**: `APP_CONFIG`
   - **Value**: `dummy_app_config_for_ci_cd_practice`

## Workflow Files

- `.github/workflows/ci.yml` - CI pipeline for testing
- `.github/workflows/cd.yml` - CD pipeline for deployment

## Testing the CI/CD

### Test CI (Pull Request)
1. Create a feature branch: `git checkout -b feature/test`
2. Make changes and commit
3. Push branch: `git push -u origin feature/test`
4. Create a pull request to `main` or `develop`
5. CI will automatically run tests

### Test CD (Push)
1. After setting up secrets, push to `main` or `develop`
2. CD will automatically run simulated deployment

## Technology Stack
- Java 25
- Spring Boot 4.1.0
- Maven
- GitHub Actions
