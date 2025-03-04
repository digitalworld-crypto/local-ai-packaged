# Self-hosted AI Package

**Self-hosted AI Package** is a Docker Compose-based template that quickly deploys a complete local AI and low-code development environment. This setup includes Ollama for local LLMs, Open WebUI for interacting with AI agents, Supabase for database management, Qdrant for vector storage, and Flowise for AI workflow automation.

This version enhances the original with additional services like Supabase, Open WebUI, and Flowise. Postgres has been removed, as Supabase provides its own database.

## Features

✅ [**Self-hosted n8n**](https://n8n.io/) - Low-code platform with 400+ integrations and AI automation

✅ [**Supabase**](https://supabase.com/) - Open-source database and authentication solution

✅ [**Ollama**](https://ollama.com/) - Cross-platform local LLM management

✅ [**Open WebUI**](https://openwebui.com/) - ChatGPT-like UI for interacting with AI models

✅ [**Flowise**](https://flowiseai.com/) - No/low-code AI agent builder

✅ [**Qdrant**](https://qdrant.tech/) - High-performance open-source vector database

## Prerequisites

Before proceeding, ensure you have the following installed:

- [Python](https://www.python.org/downloads/) - Required for script execution
- [Git](https://git-scm.com/) - For repository management
- [Docker](https://www.docker.com/) - Required to run services

## Installation

Clone the repository and navigate into it:
```sh
git clone https://github.com/coleam00/local-ai-packaged.git
cd local-ai-packaged
```

### Configure Environment Variables

1. Copy `.env.example` to `.env` in the root directory:
   ```sh
   cp .env.example .env
   ```
2. Edit `.env` and set required variables:
   ```sh
   N8N_ENCRYPTION_KEY=
   N8N_USER_MANAGEMENT_JWT_SECRET=
   POSTGRES_PASSWORD=
   JWT_SECRET=
   ANON_KEY=
   SERVICE_ROLE_KEY=
   DASHBOARD_USERNAME=
   DASHBOARD_PASSWORD=
   POOLER_TENANT_ID=
   ```
   Ensure all secrets are securely generated.

## Running the Services

To start the environment, use the `start_services.py` script. The `--profile` flag specifies the compute profile:

### NVIDIA GPU Users
```sh
python3 start_services.py --profile gpu-nvidia
```

### AMD GPU Users on Linux
```sh
python3 start_services.py --profile gpu-amd
```

### CPU-only Execution (Mac & Other Systems)
```sh
python3 start_services.py --profile cpu
```

## Quick Start Guide

1. Open [n8n](http://localhost:5678/) to configure the automation workflows.
2. Open [Open WebUI](http://localhost:3000/) to interact with AI models.
3. Open Flowise at `http://localhost:3001/` for no-code AI automation.
4. Configure connections:
   - Ollama API: `http://ollama:11434`
   - Qdrant API: `http://qdrant:6333`
   - Supabase: Use credentials from `.env`

## Upgrading

To pull and restart with the latest updates:
```sh
docker compose -p localai down

docker compose -p localai pull

python3 start_services.py --profile cpu
```

## Troubleshooting

- **Supabase Issues**: Ensure there are no invalid characters in `POSTGRES_PASSWORD`.
- **GPU Support Issues**: Ensure Docker has access to your GPU (NVIDIA or AMD).
- **Service Unavailable Errors**: Ensure `.env` contains valid credentials and the services are up.

## Additional Resources
- [Supabase Self-Hosting Guide](https://supabase.com/docs/guides/self-hosting/docker)
- [Ollama Docker Instructions](https://github.com/ollama/ollama/blob/main/docs/docker.md)
- [Flowise AI Documentation](https://flowiseai.com/)
- [n8n Documentation](https://docs.n8n.io/)

## License
This project is licensed under [Apache License 2.0](LICENSE).
