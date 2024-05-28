# CI/CD Gitlab Registry Template

This is a template repository containing a basic integration between:
- GitLab CI/CD
- GitLab (public/private) Package Registry
- GitLab Repo
- Lerna monorepo

Packages under the "packages" directory containing a valid package.json are automatically included in Lerna management.

## CI/CD

The .gitlab-ci.yml file will automatically handle the build, setup, versioning, and publishing of all packages.

It uses a custom versioning strategy "x.y.z-<commit-hash>" to allow complete automation of the process.

The pipeline will automatically publish packages accordingly to the registry, and through an automated push, it updates version tags inside the repository.

It requires a few CI/CD custom variables:
- CICD_PAT: Personal access token to allow pipeline R/W operations
- PACKAGE_SCOPE: Package scope (e.g., @lr-labs)
- PACKAGE_REGISTRY: Path to GitLab package registry repository /<group>/<repo>.git (e.g., /lr-labs/alpha)
