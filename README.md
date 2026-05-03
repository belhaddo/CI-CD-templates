---
# 🛠 CI/CD Templates Hub

This is where I keep all my GitHub Action workflows. Instead of copy-pasting the same CI/CD code into every new project, I just link back to this repo. It keeps things clean, consistent, and much easier to manage.

## 🚀 Why use this?

*   **Don't Repeat Yourself:** Fix a bug in a template here, and it’s fixed for every project using it[cite: 1].
*   **Fast Builds:** I’ve already configured caching for Maven and NPM so you don't have to wait forever for dependencies to download[cite: 1, 2].
*   **Build Once, Test Many:** We build the app first, then test that exact same file. This avoids the "it built fine but failed the test run" headache[cite: 1].
*   **Quality Built-in:** Includes automatic YAML linting to catch those annoying indentation errors before they break your pipeline.

## 📂 What's inside?

| Stack | Where is it? | What it does |
| :--- | :--- | :--- |
| **Spring Boot** | `mvn-template.yaml` | Build (skip tests) → Upload JAR → Run tests on that JAR[cite: 2]. |
| **React / TS** | `react-template.yaml` | Install → Type-check → Test → Build static files[cite: 2]. |
| **YAML Lint** | `validate-yaml.yml` | Keeps all our config files looking pretty and error-free[cite: 2]. |

## 📖 How to use it

Just point your project's workflow to one of these files using the `uses` keyword.

### For your Java projects:
```yaml
jobs:
  ci:
    uses: belhaddo/CI-CD-templates/.github/workflows/mvn-template.yaml@main
    with:
      java-version: '21' # Change this to whatever version you need