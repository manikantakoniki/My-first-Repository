# Smart Library Request Workflow (ServiceNow)

An automated, scoped ServiceNow application designed to streamline and manage the end-to-end lifecycle of library resource requests (books, digital assets, research papers, and hardware). 

This solution replaces manual email chains and spreadsheets with an intuitive Service Portal experience, dynamic approval routing, and automated fulfillment tracking.

---

## 🚀 Features

*   **Self-Service Catalog Item:** A responsive Service Portal form with dynamic auto-population based on user profiles.
*   **Dynamic Flow Designer Logic:** Automated fulfillment routing based on asset type, cost, and department.
*   **Multi-Tier Approvals:** Built-in validation rules (e.g., manager approval triggers automatically for items over a set budget).
*   **Notifications Engine:** Real-time email and system notifications alerting users of status updates (Submission, Approval, Ready for Pickup/Download).
*   **Audit Trail:** Detailed activity streaming tracking every state change from request to closure.

---

## 🛠️ Technical Architecture

### Data Model
*   **Application Scope:** `x_snc_smart_lib` (or custom configured scope)
*   **Table Configurations:** 
    *   Extends standard ServiceNow `sc_req_item` (Requested Item) and `sc_task` (Catalog Task) architectures to remain compatible with standard reporting.
*   **Key Custom Fields:**
    *   `u_resource_type` (Choice: Book, Digital License, Hardware, Journal)
    *   `u_isbn_issn` (String)
    *   `u_digital_delivery` (True/False)

### Core Components
*   **Service Catalog:** `Smart Library Request` item.
*   **Workflows:** Powered entirely via ServiceNow **Flow Designer** for modern, low-code maintenance.
*   **Client Scripts & UI Policies:** Implements dynamic UI behavior (e.g., hiding shipping fields when a digital asset is selected).

---

## 📦 Installation & Deployment

### Prerequisites
*   A ServiceNow instance (**Utah, Vancouver, Washington, or newer**).
*   Admin or `application_developer` privileges on the target instance.

### Steps to Import
1.  **Fork / Clone** this repository to your local machine or connect directly via ServiceNow Studio.
2.  In your ServiceNow instance, navigate to **System Applications > Studio**.
3.  Click **Import from Source Control**.
4.  Provide your repository URL and target branch credentials.
5.  *Alternative Method:* If deploying via update sets, navigate to **System Update Sets > Retrieved Update Sets**, upload the XML payload located in the `/dist` folder, preview, and commit.

---

## 🧪 Testing the Workflow

1.  Navigate to your instance's **Service Portal** (`/sp`).
2.  Search for **"Smart Library Request"**.
3.  Submit a test request using varying item types (e.g., test a digital license vs. a physical textbook to see varying UI logic).
4.  Impersonate the designated **Approver** or group manager to verify approval gates.
5.  Verify the generation of catalog tasks (`sc_task`) for the Library Fulfillment team assignment group.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
