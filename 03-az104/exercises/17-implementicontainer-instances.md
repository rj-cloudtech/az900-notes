# Exercise 17 Implement Container Instances
- Learning path 4.: AZ-104: Deploy and manage Azure compute resources
- Module: 4. Configure Azure Container Instances

---

## Task 1 Container Instance deployen via Docker image

Uitgevoerd via **Azure portal > Container instances > + Create**

| Setting | Value |
|---|---|
| Resource group | 17rg (nieuw) |
| Container name | 17conname |
| Region | West Europe |
| Image source | Quickstart images |
| Image | mcr.microsoft.com/azuredocs/aci-helloworld:latest (Linux) |
| DNS name label | 17dns |

Container instance logs uitgeschakeld.

---

## Task 2 Deployment testen en verifiëren

- Status: **Running**
- FQDN gekopieerd en geopend in browser
- **Welcome to Azure Container Instance** pagina zichtbaar
- Pagina meerdere keren ververst voor log entries
- Logs bekeken via **Settings > Containers > Logs** — HTTP GET requests zichtbaar

---

## Task 3 Clean up

```bash
az group delete --name 17rg --yes --no-wait
```

---
