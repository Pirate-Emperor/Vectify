# Vectify - SAP HANA Cloud Vector Engine Integration for Generative AI Use Cases

## Overview

Vectify demonstrates how to implement **Retrieval Augmented Generation (RAG)** using **SAP HANA Cloud Vector Engine**, **Langchain**, and **SAP Generative AI Hub SDK**. The project aims to embed business context into generative AI workflows, enabling enhanced AI-driven insights for use cases such as automatic reply generation and issue deduplication in business scenarios.

## Project Description

Vectify is part of the **SAGENAICITY proof-of-concept**, which includes:

- Automatic social media replies for citizens of SAGENAICITY.
- Deduplication of reported issues to streamline administrative workflows.
- More features to come...

This project showcases the power of SAP HANA Cloud's vector engine to enhance generative AI models like **GPT-4** or **GPT-35-Turbo** in real-world applications.

For more details on the SAGENAICITY proof-of-concept, visit the [project overview](https://partneredge.sap.com/en/library/education/psd/2024/jan/e_oe_te_w_PSD_WEB_00004648.html).

## Key Components

- **SAP HANA Cloud Vector Engine**: Powers the vector-based data retrieval for embedding contextual information in generative AI outputs.
- **Langchain**: Provides the framework to integrate large language models and manage data pipelines.
- **SAP Generative AI Hub SDK**: Facilitates interaction with AI models such as ADA-002 and GPT-4, using SAP’s AI core services.

## Requirements

- SAP AI Core Extended with models **ADA-002**, **GPT-4**, or **GPT-35-Turbo**.
- SAP HANA Cloud with Vector Engine enabled.
- SAP BTP Subaccount with at least 2GB free runtime memory for deployment.

## Setup Instructions

### Step 1: Clone the Repository

```bash
git clone https://github.com/Pirate-Emperor/vectify.git
cd vectify
```

### Step 2: Configure SAP AI Core Extended Credentials

Ensure that your AI Core credentials are stored in `~/.aicore/config.json` as per [these instructions](https://pypi.org/project/generative-ai-hub-sdk/). The `config.json` file should look like this:

```json
{
    "AICORE_AUTH_URL": "https://yoursubaccount.authentication.yourregion.hana.ondemand.com/oauth/token",
    "AICORE_CLIENT_ID": "your-client-id",
    "AICORE_CLIENT_SECRET": "your-client-secret",
    "AICORE_BASE_URL": "https://api.ai.prod.yourregion.hana.ondemand.com/v2",
    "AICORE_RESOURCE_GROUP": "default"
}
```

### Step 3: Create Database Configuration

In the root directory of the project, create a `config.ini` file with your SAP HANA Cloud credentials:

```ini
[database]
address = 2f2e34c5-876d-9876-a3f1-d54dfc11df42.hana.prod-eu12.hanacloud.ondemand.com
port = 443
user = DBADMIN
password = Y0urP4ssw0rd!
```

This file is required for local testing and is automatically ignored when deploying to Cloud Foundry.

### Step 4: Cloud Foundry Deployment

To deploy on **Cloud Foundry**, push the app to your SAP BTP Subaccount, then provide both AI Core and SAP HANA Cloud credentials:

```bash
cf set-env contextual-answers AICORE_AUTH_URL 'https://yoursubaccount.authentication.yourregion.hana.ondemand.com/oauth/token'
cf set-env contextual-answers AICORE_CLIENT_ID 'your-client-id'
cf set-env contextual-answers AICORE_CLIENT_SECRET 'your-client-secret'
cf set-env contextual-answers AICORE_BASE_URL 'https://api.ai.prod.yourregion.hana.ondemand.com/v2'
cf set-env contextual-answers AICORE_RESOURCE_GROUP 'default'
cf set-env contextual-answers DB_ADDRESS '2f2e34c5-876d-9876-a3f1-d54dfc11df42.hana.prod-eu12.hanacloud.ondemand.com'
cf set-env contextual-answers DB_PORT '443'
cf set-env contextual-answers DB_USER 'DBADMIN'
cf set-env contextual-answers DB_PASSWORD 'Y0urP4ssw0rd!'
cf restage contextual-answers
```

### Step 5: Scale Down Memory After Deployment

Once the staging phase is complete, you can scale down the app's memory to **128MB**:

```bash
cf scale contextual-answers -m 128M
```

## Extra Documentation

Learn more about **SAP HANA Cloud Vector Engine** [here](https://github.com/Pirate-Emperor/README.md).

## Contributing

Feel free to fork the repository, make changes, and submit pull requests. Contributions are welcome!

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Author

**Pirate-Emperor**

[![Twitter](https://skillicons.dev/icons?i=twitter)](https://twitter.com/PirateKingRahul)
[![Discord](https://skillicons.dev/icons?i=discord)](https://discord.com/users/1200728704981143634)
[![LinkedIn](https://skillicons.dev/icons?i=linkedin)](https://www.linkedin.com/in/piratekingrahul)

[![Reddit](https://img.shields.io/badge/Reddit-FF5700?style=for-the-badge&logo=reddit&logoColor=white)](https://www.reddit.com/u/PirateKingRahul)
[![Medium](https://img.shields.io/badge/Medium-42404E?style=for-the-badge&logo=medium&logoColor=white)](https://medium.com/@piratekingrahul)

- GitHub: [Pirate-Emperor](https://github.com/Pirate-Emperor)
- Reddit: [PirateKingRahul](https://www.reddit.com/u/PirateKingRahul/)
- Twitter: [PirateKingRahul](https://twitter.com/PirateKingRahul)
- Discord: [PirateKingRahul](https://discord.com/users/1200728704981143634)
- LinkedIn: [PirateKingRahul](https://www.linkedin.com/in/piratekingrahul)
- Skype: [Join Skype](https://join.skype.com/invite/yfjOJG3wv9Ki)
- Medium: [PirateKingRahul](https://medium.com/@piratekingrahul)

---
