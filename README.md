# SMS Expense Tracker AI Agent 💰

An SMS-based conversational AI expense tracker that feels like texting a brutally honest friend who actually cares about your finances. Track expenses, manage budgets, and get roasted (or hyped) based on your spending habits, all via text message.

## ✨ What Makes This Different

Unlike traditional expense tracking apps that require you to open an app, fill out forms, and categorize manually, this agent lives in your text messages. Just text what you spent like you're telling a friend, and it handles the rest. It's fast, natural, and actually engaging—you'll want to use it.

## 🎯 Core Features

### Natural Language Expense Logging
Log expenses exactly how you think about them:
- `"lunch $15"` → Logged instantly
- `"coffee $5.50 starbucks"` → Tracks merchant automatically
- `"uber $22 with tip"` → Extracts the base amount intelligently
- `"lunch $15, dinner $30"` → Handles multiple expenses in one message
- `"coffee"` → Asks for amount if you forget

The agent understands context, handles typos, and extracts amounts from natural language—no rigid formats required.

### Smart Expense Management
- **Undo & Edit**: Made a mistake? Just say `"undo"` or `"change coffee to $6"` and it's fixed instantly
- **Bulk Operations**: `"delete all coffee expenses this week"` with confirmation for safety
- **Refunds & Returns**: Track money coming back with `"refund $50"`
- **Receipt Processing with OCR**: Send a photo of your receipt and the agent uses advanced OCR technology to extract all items, amounts, and merchants automatically—no manual entry needed. The agent analyzes bills and receipts intelligently to categorize and log expenses.
- **Bill Splitting**: `"we spent $200 on dinner, 4 people, split it"` → Calculates per person instantly

### Payment & Debt Tracking
- **Venmo/Zelle/Cash App**: `"venmo'd Kabir $40 for dinner"` → Tracks who you paid
- **IOU Management**: `"i owe john $20"` → Automatically tracks debts both ways
- **Debt Queries**: `"how much do i owe Kabir?"` → Instant answer
- **Payment History**: See all transactions with specific contacts

### Intelligent Budget Management
- **Flexible Budgets**: Set daily, weekly, or monthly budgets
- **Category Budgets**: `"budget $100 for food this month"` → Tracks spending per category
- **Real-Time Alerts**: Get notified when you're approaching or exceeding budgets
- **Budget Insights**: See exactly where your money is going and how it compares to your limits

### Powerful Spending Analytics
- **Time-Based Queries**: `"how much this week?"`, `"coffee spending this month"`, `"what did I buy today?"`
- **Category Breakdowns**: See spending by category with detailed breakdowns
- **Trend Detection**: Automatically detects spending patterns and suggests improvements
- **Smart Insights**: Proactive messages like `"you usually log coffee around this time, did you forget?"`
- **Weekly Summaries**: Automated weekly spending reports delivered to your phone

### Recurring Expense Detection
- **Pattern Recognition**: Automatically detects when you log the same expense regularly
- **Recurring Setup**: `"set coffee as recurring $5 daily"` → Tracks subscriptions and habits
- **Smart Suggestions**: Suggests setting up recurring expenses based on your patterns

## 🎭 Personality & Engagement

### Multiple Personality Modes
Choose how you want to be tracked:
- **Savage Mode** (Default): Brutally honest but caring—roasts you for bad spending, celebrates wins
- **Supportive Mode**: Encouraging and understanding—gentle guidance
- **Neutral Mode**: Balanced and factual—just the numbers
- **Chaos Mode**: Unpredictable and wild—keeps things interesting

### Context-Aware Responses
The agent doesn't just log expenses—it reacts to WHAT you bought:
- Reacts differently to a $50 dinner vs $50 coffee
- Calls out patterns: `"this is coffee #12 this week bro… unhinged af ☕💀"`
- Celebrates wins: `"yo day 5 streak of staying under budget! 🔥"`
- Provides encouragement when you're doing well

### Engagement Features
- **Streak Tracking**: Build streaks for staying under budget (Day 1, 5, 10, 30+ milestones)
- **Achievement System**: Unlock achievements for financial milestones
- **Easter Eggs**: Hidden messages and callouts for special situations
- **Inactive Check-Ins**: Friendly messages if you haven't logged in a while

## 🤖 Agentic Workflow

This isn't just a chatbot—it's an intelligent agent that works proactively:

- **Autonomous Decision Making**: The agent analyzes your spending patterns and makes intelligent suggestions without you asking
- **Contextual Awareness**: Remembers your entire conversation history and spending patterns to provide relevant insights
- **Proactive Interventions**: Detects when you're overspending or forgetting to log expenses and reaches out
- **Multi-Step Reasoning**: Handles complex queries like "how much did I spend on coffee this month compared to last month?" by analyzing multiple data points
- **Adaptive Learning**: Learns your spending habits and adjusts responses accordingly
- **Goal-Oriented**: Works towards helping you achieve your financial goals through intelligent guidance

The agent doesn't just respond—it thinks, analyzes, and acts in your best interest.

## 🚀 Advanced Features

### Smart Suggestions & Reminders
- **Time-Based Reminders**: `"you usually log coffee around this time, did you forget?"`
- **Category Reminders**: Notices when you haven't logged a frequent category
- **Pattern Callouts**: `"your main character purchase is: coffee. that's your villain origin story fr."`
- **Weekly Wraps**: `"you're at $102 on coffee this week. caffeine addiction arc going crazy."`

### Intelligent Error Handling
- **Typo Correction**: `"coffe $5"` → Automatically corrects to `"coffee"`
- **Amount Parsing**: Handles `"$5"`, `"5 bucks"`, `"five dollars"`, `"$5 with tip"` seamlessly
- **Partial Expenses**: If you forget the amount, it asks: `"how much was that coffee?"`
- **Context Awareness**: Remembers what you're talking about across messages

### Privacy & Control
- **Complete Data Isolation**: Each user's data is completely separate and secure
- **Opt-Out Options**: Control what messages you receive (check-ins, achievements, summaries)
- **Data Export**: Export your expenses anytime
- **Two-Step Deletion**: Safe data deletion with confirmation

## 📱 How It Works

1. **Text Your Expenses**: Just text what you spent like you're telling a friend
2. **AI Processes**: The agent understands context, extracts details, and categorizes automatically
3. **Get Insights**: Receive real-time feedback, budget updates, and spending insights
4. **Track Patterns**: See trends, get suggestions, and build better financial habits

No app to download. No forms to fill. No categories to remember. Just text.

## 🛠️ Technical Stack

- **Backend**: Python 3.11+, FastAPI
- **Database**: PostgreSQL (Supabase)
- **AI**: Advanced language model for natural language understanding
- **SMS**: Twilio for reliable message delivery
- **Deployment**: Cloud-ready, scales automatically

## 📋 Quick Start

### Prerequisites
- Python 3.11+
- PostgreSQL database (Supabase recommended)
- Twilio account with phone number
- API keys for AI services

### Installation

```bash
# Clone repository
git clone https://github.com/kabirrgrover/sms-expense-tracker-public.git
cd sms-expense-tracker-public

# Install dependencies
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your credentials

# Set up database
# Run SQL schema files in order in your database

# Start server
python main.py
```

### Configuration

Set up your `.env` file with:
- Twilio credentials (Account SID, Auth Token, Phone Number)
- Database connection string
- AI service API keys

### Twilio Webhook Setup

1. Deploy your server (or use ngrok for local development)
2. In Twilio Console → Phone Numbers → Your Number
3. Set webhook URL to your server's `/sms` endpoint
4. Set HTTP method to `POST`

## 💡 Usage Examples

### Basic Expense Logging
```
You: lunch $15
Bot: $15 on lunch logged 💀 you've spent $45 on food this week

You: coffee $5.50 starbucks
Bot: $5.50 at starbucks logged. that's coffee #8 this week bro ☕

You: uber $22 with tip
Bot: $22 on transport logged. logged 💀
```

### Budget Management
```
You: budget $500 this month
Bot: monthly budget set to $500. let's see if you can stick to it 👀

You: budget $100 for food this month
Bot: monthly food budget set to $100. tracking that now 🍽️

You: how much left in my food budget?
Bot: you've spent $85 on food this month. $15 left in your budget. cutting it close 👀
```

### Spending Queries
```
You: how much this week?
Bot: you've spent $135 this week. breakdown: $85 food, $30 transport, $20 coffee

You: what did I buy today?
Bot: today's expenses:
- $15 lunch
- $5.50 coffee
- $22 uber
total: $42.50

You: coffee spending this month
Bot: you dropped $94 on coffee this month. that's a lot of caffeine 💀
```

### Debt & Payment Tracking
```
You: i owe john $20
Bot: logged. you owe john $20 now 👍

You: john paid me back $20
Bot: updated. john paid you back. balance cleared 💀

You: how much do i owe Kabir?
Bot: you owe Kabir $40 total
```

### Receipt Processing with OCR
```
You: [sends photo of receipt]
Bot: extracted from receipt:
- $15.50 lunch
- $3.25 coffee
- $2.00 tip
logged all items 💀
```

### Advanced Features
```
You: undo
Bot: aight, i'll pretend that $15 on lunch never happened… this time.

You: change coffee to $6
Bot: updated that coffee to $6.00 👍

You: delete all coffee expenses this week
Bot: yo wait... you want to delete 8 coffee expenses this week? that's permanent. reply 'yes' to confirm
```

## 🎯 Use Cases

- **Personal Finance**: Track daily spending and build better habits
- **Budgeting**: Set budgets and get real-time alerts
- **Debt Management**: Track who owes whom and manage IOUs
- **Expense Reports**: Generate spending summaries for work or personal use
- **Habit Tracking**: See patterns in your spending and make informed decisions

## 🔒 Security & Privacy

- **End-to-End Encryption**: Conversation history encrypted at rest
- **Data Isolation**: Complete separation between users
- **No Data Sharing**: Your data stays yours
- **Secure Infrastructure**: Built on enterprise-grade platforms
- **Rate Limiting**: Prevents abuse and spam

## 🚀 Production Ready

This is a fully functional, production-grade expense tracking system. It handles:
- High message volumes
- Concurrent users
- Error recovery
- Data integrity
- Performance optimization
- Scalable architecture

## 📚 Documentation

Comprehensive documentation available for:
- Feature details and capabilities
- Security measures
- Data isolation and privacy
- API integration
- Deployment guides

## 🤝 Contributing

This is a public repository showcasing an SMS-based AI expense tracker. For questions, issues, or contributions, please open an issue or contact the repository owner.

## 📝 License

See LICENSE file for details.

## 🙏 Acknowledgments

Built with modern AI and cloud technologies to create a seamless, conversational expense tracking experience.

---

**Track your expenses. Build better habits. Text your way to financial awareness.** 💰

