# 🚀 Google Calendar Workflow Automation with n8n

This repository contains an automated workflow built using **n8n** that integrates with **Google Calendar** to manage calendar events through a webhook trigger. It's designed for scenarios like team meetings, personal reminders, scheduling apps, or travel planners.

---

## 🔄 Workflow Summary

The automation listens to an incoming HTTP POST request and performs one of the following actions on a Google Calendar:

- ✅ **Create** an event  
- 🔄 **Update** an event  
- ❌ **Delete** an event  

Each action is routed using a **Switch node** based on the `action` field in the payload, and the result is sent back to the requester via the webhook response.

---

## 📆 Example Use Case

We tested the workflow with this scenario:

**Event Title:** Karachi Breakfast and Market Visit 🥐🛒  
**Start:** July 13, 2025 – 09:00 AM PKT  
**End:** July 13, 2025 – 10:00 AM PKT  
**Description:** Exploring local food and market culture

The following `PlannerInput` data structure was used to feed the automation:

```python
demo_input = PlannerInput(
    nop=5,
    interests=["team", "meeting"],
    startDate="2025-07-13T09:00:00+05:00",
    endDate="2025-07-13T10:00:00+05:00",
    cuisine="Italian",
    locations=["Karachi"],
    budget="5000",
    title="Karachi Breakfast and Market Visit",
    description="Exploring local food and market culture"
)
```

---

## 📦 Payload Format (Webhook Request)

Send a POST request to the webhook URL with JSON like this:

```json
{
  "action": "create",
  "summary": "Karachi Breakfast and Market Visit",
  "description": "Exploring local food and market culture",
  "start": "2025-07-13T04:00:00.000Z",
  "end": "2025-07-13T05:00:00.000Z"
}
```

> Note: The time should be in **UTC ISO 8601** format.

Supported `action` values:
- `"create"` – to create a new event  
- `"update"` – to update an existing event (requires `eventId`)  
- `"delete"` – to delete an event (requires `eventId`)  

---

## 🔧 Tools & Technologies

- 🌐 **n8n**: No-code workflow automation  
- 🗓️ **Google Calendar API**: For creating, updating, deleting events  
- 🛰️ **Webhooks**: Trigger automation from external systems  
- 🔀 **Switch Node**: Rule-based routing of logic  

---

## 🛠️ Setup Instructions

1. **Clone this repository** to your local or cloud workspace.  
2. **Import the provided workflow JSON** into your n8n instance.  
3. **Set up Google Calendar credentials** in n8n:  
   - Use OAuth2 with `calendar.events` scope.  
   - Authenticate your account.  
4. Replace the default **Webhook URL** with the one generated in your instance.  
5. Activate the workflow.  
6. Use Postman, Curl, or any app to send a POST request to the webhook.  

---

## 🤖 Sample Use Cases

- Booking system backend  
- Personal assistant bots  
- Team or office meeting scheduler  
- Travel planning automation  
- Integration with chatbots  

---

## 🔐 Security Note

- Ensure only trusted sources can access the webhook URL.  
- Use environment variables or credential managers for sensitive data.  

---

## 📎 License

This project is licensed under the **MIT License** — free to use, modify, and share.

---

**Built with ❤️ using n8n and the power of the open source automation ecosystem.**

#Automation #n8n #NoCode #GoogleCalendar #Workflow #Webhooks #Integration #SoftwareEngineering #OpenSource #Productivity
