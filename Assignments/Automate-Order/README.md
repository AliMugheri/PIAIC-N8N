# Order-Automation Workflow

This repository contains an **n8n workflow** that automates order processing, tracking, and reporting between a custom ERP system, Airtable, and Discord.

---

## 📌 Overview

The workflow is designed to:

- ⏰ Run **every Monday at 9 AM** automatically.  
- 🌐 Fetch order data from the internal ERP system.  
- ✅ Check order status (`processing`).  
- 📊 Store order details in **Airtable**.  
- ➕ Calculate **weekly totals** (number of orders + total value).  
- 📢 Send a **summary message** to **Discord**.  

---

## ⚙️ Workflow Steps

1. **Schedule Trigger** → Runs weekly on Monday at 9 AM.  
2. **HTTP Request** → Gets order data from ERP (with authentication).  
3. **If Condition** → Filters orders with status `processing`.  
4. **Edit Fields** → Prepares data (orderID, employeeName).  
5. **Create Record (Airtable)** → Saves order into Airtable.  
6. **Code Node (JavaScript)** → Calculates totals:
   - `totalBooked` = number of orders  
   - `bookedSum` = total value  
7. **Discord** → Posts a summary message with totals and unique ID.  

---

## 🔑 Credentials Required

To set up the workflow, configure these credentials in n8n:

- **HTTP Header Auth** → to access the ERP system.  
- **Airtable Personal Access Token** → to insert records.  
- **Discord Webhook** → to post messages.  

---

## 📂 File

- `order-automation.json` → exported n8n workflow file.  

**How to import into n8n:**
1. Go to **Workflows** → **Import from File**.  
2. Upload `order-automation.json`.  
3. Set up credentials for ERP, Airtable, and Discord.  
4. Activate the workflow.  

---

## 🚀 Usage

- Workflow runs automatically each week.  
- You can also **trigger manually** from n8n.  
- Check **Airtable** for stored orders.  
- Check **Discord** for weekly reports.  

---
