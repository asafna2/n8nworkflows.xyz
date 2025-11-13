# n8nworkflows.xyz

Standalone and versionable archive of n8n workflows from the official [n8n.io/workflows](https://n8n.io/workflows) website. This repository allows you to preserve, version, and reuse workflow templates in minimal format, ready to be imported offline.

[n8nworkflows.xyz](https://n8nworkflows.xyz)

---

## 📋 Table of Contents

- [Repository Structure](#-repository-structure)
- [Archived Workflow Format](#-archived-workflow-format)
- [Usage](#-usage)
- [Workflows Summary](#-workflows-summary)
- [License](#-license)

---

## 📁 Repository Structure

```
n8nworkflows.xyz/
├── archive/
│   └── workflows/
│       ├── workflow-name-id-1/
│       │   ├── readme.md
│       │   ├── workflow.json
│       │   ├── metadata.json
│       │   └── workflow-name-id-1.webp
│       ├── workflow-name-id-2/
│       │   └── ...
│       └── ...
└── README.md
```

Each workflow is isolated in its own folder to facilitate navigation, versioning, and individual import.

---

## 📄 Archived Workflow Format

Each workflow folder contains **exactly 4 files**:

| File | Description |
|:---|:---|
| **`readme.md`** | Complete workflow description in Markdown (original template's `readme` field) |
| **`workflow.json`** | Raw workflow export in JSON format, ready to be imported into n8n |
| **`metadata.json`** | Metadata: author (`user_*`), tags, creation date, public link to `https://n8n.io/workflows/<workflowId>` |
| **`<slug-and-id>.webp`** | Workflow screenshot (hero image from Supabase `worklowscreenshot` bucket) |

---



## 📚 Workflows Summary (50 workflows)

- [AI Agents can Create, Enrich leads with this Lemlist Tool MCP Server-5233]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/AI%20Agents%20can%20Create%2C%20Enrich%20leads%20with%20this%20Lemlist%20Tool%20MCP%20Server-5233")
- [AI Podcast Generator with RSS Feed & ElevenLabs Voice-5084]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/AI%20Podcast%20Generator%20with%20RSS%20Feed%20%26%20ElevenLabs%20Voice-5084")
- [AI-Powered Knowledge Assistant using Google Sheets, OpenAI, and Supabase Vector Search-4477]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/AI-Powered%20Knowledge%20Assistant%20using%20Google%20Sheets%2C%20OpenAI%2C%20and%20Supabase%20Vector%20Search-4477")
- [Auto-Post Breaking News Content Using Perplexity AI to X (Twitter)-3822]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Auto-Post%20Breaking%20News%20Content%20Using%20Perplexity%20AI%20to%20X%20(Twitter)-3822")
- [Automate Lead Nurturing & Follow-Up with Gmail, Twilio SMS & GoHighLevel-4027]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Automate%20Lead%20Nurturing%20%26%20Follow-Up%20with%20Gmail%2C%20Twilio%20SMS%20%26%20GoHighLevel-4027")
- [Automate Shopify Orders from Airtable with Gmail Confirmations-9448]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Automate%20Shopify%20Orders%20from%20Airtable%20with%20Gmail%20Confirmations-9448")
- [AWS Azure GCP Multi-Cloud Cost Monitoring & Alerts for Budget Control-7374]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/AWS%20Azure%20GCP%20Multi-Cloud%20Cost%20Monitoring%20%26%20Alerts%20for%20Budget%20Control-7374")
- [Baserow campaign database to Shopify with image upload & dynamic template update-2186]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Baserow%20campaign%20database%20to%20Shopify%20with%20image%20upload%20%26%20dynamic%20template%20update-2186")
- [Bidirectional ClickUp Task & Google Calendar Sync with Multi-Calendar Routing-7871]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Bidirectional%20ClickUp%20Task%20%26%20Google%20Calendar%20Sync%20with%20Multi-Calendar%20Routing-7871")
- [Build a RAG System with Automatic Citations using Qdrant, Gemini & OpenAI-5023]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Build%20a%20RAG%20System%20with%20Automatic%20Citations%20using%20Qdrant%2C%20Gemini%20%26%20OpenAI-5023")
- [Build a Support Ticket Analytics Dashboard with ScrapeGraphAI, Google Sheets & Slack Alerts-6431]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Build%20a%20Support%20Ticket%20Analytics%20Dashboard%20with%20ScrapeGraphAI%2C%20Google%20Sheets%20%26%20Slack%20Alerts-6431")
- [Check Email via AI agent with Mailcheck Tool MCP Server-5208]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Check%20Email%20via%20AI%20agent%20with%20Mailcheck%20Tool%20MCP%20Server-5208")
- [Check for preview for a link -935]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Check%20for%20preview%20for%20a%20link%20-935")
- [Complete Zendesk API Integration with MCP Server for AI Agents-5057]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Complete%20Zendesk%20API%20Integration%20with%20MCP%20Server%20for%20AI%20Agents-5057")
- [Convert n8n tags into folders and move workflows-3445]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Convert%20n8n%20tags%20into%20folders%20and%20move%20workflows-3445")
- [Create .SRT Subtitles & .LRC Lyrics from Audio with Whisper AI and GPT-5-nano-9589]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Create%20.SRT%20Subtitles%20%26%20.LRC%20Lyrics%20from%20Audio%20with%20Whisper%20AI%20and%20GPT-5-nano-9589")
- [Create a Voice & Text Telegram Assistant with Lookio RAG and GPT-4.1-9870]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Create%20a%20Voice%20%26%20Text%20Telegram%20Assistant%20with%20Lookio%20RAG%20and%20GPT-4.1-9870")
- [Create Images from Text Prompts using Flux Schnell and Replicate-6780]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Create%20Images%20from%20Text%20Prompts%20using%20Flux%20Schnell%20and%20Replicate-6780")
- [Daily Competitor Research Automation using SerpAPI, Google Sheets & Airtable-7313]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Daily%20Competitor%20Research%20Automation%20using%20SerpAPI%2C%20Google%20Sheets%20%26%20Airtable-7313")
- [Daily Crypto Market Report with CoinGecko, WhatsApp, and Email Alerts-7729]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Daily%20Crypto%20Market%20Report%20with%20CoinGecko%2C%20WhatsApp%2C%20and%20Email%20Alerts-7729")
- [Daily MLB Pitcher vs. Batter Matchup Analysis with Google Sheets and Telegram-7252]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Daily%20MLB%20Pitcher%20vs.%20Batter%20Matchup%20Analysis%20with%20Google%20Sheets%20and%20Telegram-7252")
- [Display ServiceNow Incident Details in Slack using Slash Commands-2727]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Display%20ServiceNow%20Incident%20Details%20in%20Slack%20using%20Slash%20Commands-2727")
- [Explore n8n Nodes in a Visual Reference Library-3891]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Explore%20n8n%20Nodes%20in%20a%20Visual%20Reference%20Library-3891")
- [Export Cloudflare Domains with DNS Records and Settings to Google Sheets-4850]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Export%20Cloudflare%20Domains%20with%20DNS%20Records%20and%20Settings%20to%20Google%20Sheets-4850")
- [Extract Tasks from Telegram Messages to Notion using Gemini AI and Approvals-9271]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Extract%20Tasks%20from%20Telegram%20Messages%20to%20Notion%20using%20Gemini%20AI%20and%20Approvals-9271")
- [Find Recipes Using API Ninjas with Interactive Form Interface-7835]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Find%20Recipes%20Using%20API%20Ninjas%20with%20Interactive%20Form%20Interface-7835")
- [Full Blog Content Automation with GPT-4, Claude & Ghost CMS Publisher-7920]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Full%20Blog%20Content%20Automation%20with%20GPT-4%2C%20Claude%20%26%20Ghost%20CMS%20Publisher-7920")
- [Generate Daily Sales Reports from Google Sheets with Formatted Email Summaries-6370]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Generate%20Daily%20Sales%20Reports%20from%20Google%20Sheets%20with%20Formatted%20Email%20Summaries-6370")
- [Generate Personalized and Aggregate Survey Reports with Jotform and Gemini AI-9484]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Generate%20Personalized%20and%20Aggregate%20Survey%20Reports%20with%20Jotform%20and%20Gemini%20AI-9484")
- [Get notified on Gmail, Telegram and Slack on new Stripe purchase-3410]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Get%20notified%20on%20Gmail%2C%20Telegram%20and%20Slack%20on%20new%20Stripe%20purchase-3410")
- [Gmail Cold Email Sequence with Google Sheets Tracking & Slack Notifications-5000]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Gmail%20Cold%20Email%20Sequence%20with%20Google%20Sheets%20Tracking%20%26%20Slack%20Notifications-5000")
- [Gmail Email Auto-Organizer with Google Sheets Rules-8333]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Gmail%20Email%20Auto-Organizer%20with%20Google%20Sheets%20Rules-8333")
- [Google services (Sheets/Drive/Gmail) instead of 'Google Suite'-10387]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Google%20services%20(Sheets%2FDrive%2FGmail)%20instead%20of%20'Google%20Suite'-10387")
- [IP Reputation Check & SOC Alerts with Splunk, VirusTotal and AlienVault-6037]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/IP%20Reputation%20Check%20%26%20SOC%20Alerts%20with%20Splunk%2C%20VirusTotal%20and%20AlienVault-6037")
- [Lead Analysis & Personalized Email Generation with OpenAI, Firecrawl & gotoHuman-8520]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Lead%20Analysis%20%26%20Personalized%20Email%20Generation%20with%20OpenAI%2C%20Firecrawl%20%26%20gotoHuman-8520")
- [Malicious File Detection & Response: Wazuh to VirusTotal with Slack Alerts-5997]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Malicious%20File%20Detection%20%26%20Response%3A%20Wazuh%20to%20VirusTotal%20with%20Slack%20Alerts-5997")
- [Meta Ads Performance Analysis with GPT-4 & Gemini AI Comparisons-6545]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Meta%20Ads%20Performance%20Analysis%20with%20GPT-4%20%26%20Gemini%20AI%20Comparisons-6545")
- [Monitor Brand Mentions on X with Gemini AI Visual Analysis & Telegram Alerts-8355]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Monitor%20Brand%20Mentions%20on%20X%20with%20Gemini%20AI%20Visual%20Analysis%20%26%20Telegram%20Alerts-8355")
- [Monitor Flight Price Drops and Send Email Alerts with SerpAPI and Gmail-6503]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Monitor%20Flight%20Price%20Drops%20and%20Send%20Email%20Alerts%20with%20SerpAPI%20and%20Gmail-6503")
- [Monitor Website Uptime with Gmail Alerts-5887]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Monitor%20Website%20Uptime%20with%20Gmail%20Alerts-5887")
- [Predict End of Utterance for smoother AI agent chats with Telegram and Gemini-5014]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Predict%20End%20of%20Utterance%20for%20smoother%20AI%20agent%20chats%20with%20Telegram%20and%20Gemini-5014")
- [Publish image & video to multiple social media (X, Instagram, Facebook and more)-3669]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Publish%20image%20%26%20video%20to%20multiple%20social%20media%20(X%2C%20Instagram%2C%20Facebook%20and%20more)-3669")
- [Real-Time Crypto Price Bot for Telegram with Gemini AI & CoinGecko-9230]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Real-Time%20Crypto%20Price%20Bot%20for%20Telegram%20with%20Gemini%20AI%20%26%20CoinGecko-9230")
- [Scrape Product Info from Website URLs in Google Sheets using Dumpling AI-6950]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Scrape%20Product%20Info%20from%20Website%20URLs%20in%20Google%20Sheets%20using%20Dumpling%20AI-6950")
- [Simple Google indexing Workflow in N8N-2123]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Simple%20Google%20indexing%20Workflow%20in%20N8N-2123")
- [Streamline data from an n8n form into Google Sheet, Airtable and Email Sending-2087]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Streamline%20data%20from%20an%20n8n%20form%20into%20Google%20Sheet%2C%20Airtable%20and%20Email%20Sending-2087")
- [Tesla Quant Technical Indicators Webhooks Tool-4095]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Tesla%20Quant%20Technical%20Indicators%20Webhooks%20Tool-4095")
- [Validate and Create LEDGERS Contacts from Google Sheets with Error Handling-4961]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/Validate%20and%20Create%20LEDGERS%20Contacts%20from%20Google%20Sheets%20with%20Error%20Handling-4961")
- [⚡📽️ Ultimate AI-Powered Chatbot for YouTube Summarization & Analysis-2956]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/%E2%9A%A1%F0%9F%93%BD%EF%B8%8F%20Ultimate%20AI-Powered%20Chatbot%20for%20YouTube%20Summarization%20%26%20Analysis-2956")
- [🚀 TikTok Video Automation Tool ✨ – Highly Optimized with OpenAI & Replicate-3004]("https://github.com/nusquama/n8nworkflows.xyz/tree/main/workflows/%F0%9F%9A%80%20TikTok%20Video%20Automation%20Tool%20%E2%9C%A8%20%E2%80%93%20Highly%20Optimized%20with%20OpenAI%20%26%20Replicate-3004")

---

## 🔗 Useful Links

- 🌐 [n8nworkflows.xyz website](https://n8nworkflows.xyz)
- 📖 [Official n8n Documentation](https://docs.n8n.io)
- 💬 [n8n Community](https://community.n8n.io)
- 🐙 [n8n on GitHub](https://github.com/n8n-io/n8n)

---

## 📝 License

This repository archives public workflows from [n8n.io/workflows](https://n8n.io/workflows). Each workflow retains its original license. Refer to individual metadata for more information.

The archiving code and repository structure are licensed under [MIT](LICENSE).

---

## ⚠️ Disclaimer

This project is **independent** and not officially affiliated with n8n. It is a personal initiative aimed at facilitating access to and preservation of public n8n workflows.

---

**Made with ❤️ for the n8n community**

