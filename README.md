# DevOps CI/CD Workshop: Jenkins + Grafana + Katalon

## Langkah:
1. Edit file di VS Code
2. Commit & push ke GitHub
3. Jenkins akan pull otomatis dan deploy Grafana
4. Testing dilakukan melalui Katalon Studio

## Struktur:
- Dockerfile: untuk build image Grafana
- jenkins/Jenkinsfile: pipeline CI/CD
- katalon/: isi test case manual di Katalon lokal
