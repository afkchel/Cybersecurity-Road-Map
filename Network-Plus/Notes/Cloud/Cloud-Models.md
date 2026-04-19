# ☁️ Cloud Service & Deployment Models

This note covers the different ways cloud infrastructure is managed and the shared responsibility between providers and customers.

---

## 🏗️ Cloud Deployment Models


| Model | Description | Access |
| :--- | :--- | :--- |
| **Public Cloud** | Infrastructure available to everyone over the internet. | Global / Public |
| **Private Cloud** | A virtualized local data center for internal use only. | Internal / Private |
| **Hybrid Cloud** | A combination of both public and private cloud configurations. | Mixed |

---

## 🛠️ Cloud Service Models

### 1. Software as a Service (SaaS)
*   **Concept:** On-demand software. No local installation or management required.
*   **Essentially:** **Just log in and use it.** The provider manages the app, updates, and infrastructure.
*   **Examples:** Google Mail (Gmail), Office 365.
*   **Pros:** Centralized management of data and applications.

### 2. Infrastructure as a Service (IaaS)
*   **Concept:** Also known as **Hardware as a Service (HaaS)**. You rent the computing power and storage.
*   **Essentially:** **You provide the software.** You are responsible for installing the OS, managing applications, and handling security updates.
*   **Examples:** Web hosting providers where you rent a raw server.
*   **Pros:** Maximum control over data and security.

### 3. Platform as a Service (PaaS)
*   **Concept:** A middle ground where the provider gives you the "building blocks" to create an app.
*   **Essentially:** **You build the app, they manage the engine.** You handle the development while the provider manages the underlying platform.
*   **Examples:** Salesforce.com (tools to build custom CRM apps).

---

**Key Takeaway:** Regardless of the model (SaaS, PaaS, or IaaS), the **Customer** is always responsible for their own data, accounts, and devices.
