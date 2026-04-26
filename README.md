# 📌 Gmail Auto-Clean Automation using n8n #

Managing a cluttered inbox is time-consuming and often leads to missing important emails. This project solves that problem by building an automated workflow in n8n that filters and organizes low-priority emails in Gmail.

The workflow runs on a scheduled basis and identifies unread emails from categories such as Promotions, Social, and Updates. Instead of deleting them directly, it assigns a custom label (Auto-Clean), allowing users to review and manage these emails later in a structured way.

This ensures that important conversations remain untouched while unnecessary emails are separated automatically.

## 🎯 Problem Statement ##

Modern inboxes are flooded with promotional, social, and update emails. Manually sorting them:

Wastes time
Reduces productivity
Increases chances of missing important emails

## 💡 Solution ##

An automated n8n workflow that:

Fetches emails from Gmail
Filters based on unread status and category
Segregates low-priority emails
Applies a custom label for easy tracking and cleanup

## ⚙️ Workflow Overview ##

Schedule Trigger
Executes the workflow daily at a fixed time (9 AM)
Fetch Emails (Gmail Node)
Retrieves recent emails from the inbox
IF Condition Node
Filters emails where:
Status = Unread
Category = Promotions / Social / Updates
Excludes Sent emails
Labeling Node
Adds a custom label (Auto-Clean) to filtered emails

### 🧠 Logic Used ###

The workflow uses conditional filtering to ensure only relevant emails are processed:

{{ 
  $json["labelIds"].includes("UNREAD") &&
  !$json["labelIds"].includes("SENT") &&
  (
    $json["labelIds"].includes("CATEGORY_PROMOTIONS") ||
    $json["labelIds"].includes("CATEGORY_SOCIAL") ||
    $json["labelIds"].includes("CATEGORY_UPDATES")
  )
}}

## 🛠️ Tech Stack ##
n8n (Workflow Automation)
Gmail API
CMD


## 📊 Use Case ##
This workflow is useful for:

Professionals managing high email volume
Students receiving bulk updates and promotions
Anyone looking to maintain a clean and organized inbox

## 📈 Impact ##
Saves daily manual effort
Improves email management efficiency
Helps focus on important communication

## 🔧 How to Use ##
Import the provided JSON workflow into n8n
Connect your Gmail account
Set the schedule trigger
Activate the workflow

## 🔮 Future Improvements ##
Auto-delete emails after a defined period
Add priority-based filtering
Slack/notification alerts for important emails
Dashboard for tracking email categories


