
# 📁 rahmah-static-content

**Static content repository** for the **Rahmah Muslim Marriage App**, designed to integrate seamlessly with the [`collection`](https://github.com/olivium-dev/collection) microservice.

This repository contains versioned and structured JSON files representing dynamic collections (e.g., countries, professions, interests) to be consumed as APIs by the `collection` microservice. Each file in this repository is automatically transformed into a RESTful API endpoint and exposed with full OpenAPI/Swagger documentation via the collection service.

----------

## 🔧 Purpose

This repository is **not** a standalone project. It is designed to **hold static content** that is consumed by the [`collection`](https://github.com/olivium-dev/collection) microservice in the [Rahmah](https://rahmah.app) platform.

At **build-time**, the `collection` service:

-   Fetches this repo’s JSON files via GitHub API.
    
-   Dynamically generates RESTful endpoints for each file.
    
-   Publishes OpenAPI documentation for all collections.
    

----------

## 📁 Repository Structure

Each JSON file placed at the root or inside a folder represents an API resource. For example:

bash

CopyEdit

`rahmah-static-content/
├── countries.json # GET /collection/countries ├── interests.json # GET /collection/interests └── filters/
    └── age_groups.json # GET /collection/filters/age_groups` 

----------

## 🔄 How It Works

-   Every `.json` file becomes a public API.
    
-   Changes to any file must trigger the rebuild of the `collection` service.
    
-   The `collection` service automatically syncs the content and exposes them via endpoints.
    

----------

## ✅ Workflow After Any Change

When you modify or add any JSON file in this repository:

### 1. Commit your changes to `main`:

bash

CopyEdit

`git add .
git commit -m "Update country list" git push origin main` 

### 2. Manually Trigger the Deployment Pipeline

To reflect changes in the Rahmah environment, you **must manually trigger** the `collection` service pipeline:

➡️ [Run "Deploy to EC2 Rahmah"](https://github.com/olivium-dev/collection/actions/workflows/deploy-to-ec2-rahmah.yml)

----------

## 🧪 Validation Tips

Before pushing changes:

-   Ensure your JSON is **well-formed** and **UTF-8 encoded**.
    
-   Use online JSON validators or run:
    

bash

CopyEdit

`python -m json.tool yourfile.json` 

----------

## 🤖 Linked Microservice: Collection

The `collection` microservice fetches this repository and handles:

-   📥 Automatic synchronization with this content
    
-   🧠 Intelligent dynamic endpoint generation
    
-   📜 Auto-generated Swagger/OpenAPI documentation
    
-   🧱 Schema evolution support
    

Learn more: [Collection Microservice README](https://github.com/olivium-dev/collection)

----------

## 💡 Best Practices

-   Keep file names lowercase and underscore-separated (e.g., `marital_status.json`).
    
-   Structure nested data where appropriate.
    
-   Document each JSON key-value clearly in accompanying PR descriptions.
    

----------

## 👥 Contributors

-   Olivium Dev Team
    
-   Community & Open Source Supporters
    

----------

## 📜 License

This project is proprietary and maintained by **Olivium Dev**. Unauthorized usage is prohibited.

----------

Let me know if you'd like a version in Arabic or if you want to include an example JSON schema template for contributors.
