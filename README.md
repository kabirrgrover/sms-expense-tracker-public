# SMS Expense Tracker AI Agent 💰

An SMS-based conversational AI expense tracker that feels like texting a brutally honest friend who actually cares about your finances. Track expenses, manage budgets, and get roasted (or hyped) based on your spending habits—all via text message.

## ✨ Features

### Core Functionality
- **Natural Language Expense Logging**: "lunch $15", "coffee $5.50 starbucks"
- **Payment Tracking**: Remember Venmo/Zelle/Cash App transactions with contact names
- **Debt/IOU Tracking**: Track who owes whom with automatic calculations
- **Budget Management**: Set daily, weekly, or monthly budgets (overall or category-specific)
- **Spending Queries**: "how much this week?", "coffee spending this month"
- **Bill Splitting**: "we spent $200 on dinner, 4 people, split it"

### Personality & Engagement
- **Multiple Personality Modes**: Savage, Supportive, Neutral, Chaos
- **Context-Aware Responses**: Reacts to WHAT you bought, not just how much
- **Budget Awareness**: Alerts when you're over budget (especially category budgets)
- **Streak Celebrations**: Day 1, 5, 10, 30 milestones
- **Easter Eggs**: Birthday month, goal achievements, $0 days
- **Custom Categories**: Create any category you want (gaming, hobbies, travel, etc.)

### Automated Features
- **Weekly Summaries**: Automated weekly spending summaries
- **Achievement Notifications**: Budget wins, $0 days
- **Inactive User Check-Ins**: Messages after 3-4 days of inactivity

### User Control
- **Opt-Out Options**: Check-ins, achievements, weekly summaries
- **Back Off**: Respects user requests for space
- **Data Deletion**: Two-step confirmation process
- **Tone Adjustment**: Automatically dials back if user is uncomfortable

## 🚀 Tech Stack

- **Backend**: Python 3.11+, FastAPI
- **Database**: PostgreSQL (Supabase)
- **AI**: OpenAI GPT-4o-mini
- **SMS**: Twilio
- **Deployment**: Any server with Python support (ngrok for local dev)

## 📋 Prerequisites

- Python 3.11+
- PostgreSQL database (Supabase recommended)
- Twilio account with phone number
- OpenAI API key
- ngrok (for local development)

## 🛠️ Setup

### 1. Clone Repository

```bash
git clone <your-repo-url>
cd RCSClutchIt
```

### 2. Install Dependencies

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Environment Variables

Create a `.env` file in the root directory:

```env
# Twilio
TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_PHONE_NUMBER=+1234567890

# Database (Supabase)
DATABASE_URL=postgresql://user:password@host:port/database

# OpenAI
OPENAI_API_KEY=your_openai_api_key
```

### 4. Database Setup

Run these SQL files in Supabase SQL Editor **in order**:

1. `schema.sql` - Base schema (users, expenses, payments, conversation_history)
2. `debts_schema.sql` - Debt/IOU tracking table
3. `budgets_schema.sql` - Budget tracking table
4. `achievements_schema.sql` - Achievement tracking and last_spending_date
5. `user_preferences_schema.sql` - User preferences and opt-outs

**Important**: If you already ran `budgets_schema.sql` before category support was added, run `budgets_category_migration.sql` to add the category column.

### 5. Start Server

```bash
# Activate virtual environment
source venv/bin/activate

# Start server
python main.py
```

Or use the provided script:

```bash
./start_server.sh
```

Server runs on `http://localhost:8080` by default.

### 6. Set Up Twilio Webhook

For local development:

1. Start ngrok: `ngrok http 8080`
2. Copy the ngrok URL (e.g., `https://abc123.ngrok-free.dev`)
3. In Twilio Console → Phone Numbers → Your Number → Messaging
4. Set webhook URL to: `https://your-ngrok-url.ngrok-free.dev/sms`
5. Set HTTP method to `POST`

## 📱 Usage Examples

### Expense Logging
```
You: lunch $15
Bot: $15 on lunch. you've spent $15 on food this week 🍔

You: I also spent 120 on dinner today...
Bot: yo you dropped $120 on dinner today? what's going on, Kabir? that's a bit much 😅
```

### Budget Setting
```
You: budget $500 this month
Bot: alright, monthly budget set to $500. let's see if you can stick to it 👀

You: out of which $100 for food only
Bot: got it, monthly food budget set to $100. let's keep an eye on that 🍽️
```

### Spending Queries
```
You: how much this week?
Bot: you've spent $135 total this week. $135 on food. that's your monthly food budget already 👀

You: coffee spending this month
Bot: you dropped $94 on coffee this month. that's a lot of caffeine 💀
```

### Debt Tracking
```
You: i owe ishaan $5
Bot: alright, you owe ishaan $5. i'll keep track of that 👍

You: how much do i owe ishaan?
Bot: you owe ishaan $5.00
```

## 📁 Project Structure

```
RCSClutchIt/
├── main.py                 # FastAPI application & webhook handler
├── database.py             # Database operations
├── gpt.py                  # OpenAI GPT integration
├── prompts.py              # GPT system prompts & templates
├── guardrails.py           # Security & content filtering
├── schema.sql              # Base database schema
├── debts_schema.sql        # Debt tracking schema
├── budgets_schema.sql      # Budget tracking schema
├── achievements_schema.sql # Achievement tracking schema
├── user_preferences_schema.sql # User preferences schema
├── weekly_summary.py       # Weekly summary generation
├── check_inactive_users.py # Inactive user check-ins
├── send_weekly_summaries.py # Weekly summary sender
├── reset_user.py          # Reset specific user
├── reset_all_users.py     # Reset all users
└── requirements.txt       # Python dependencies
```

## 🔧 Configuration

### Personality Modes

Users can have different personality modes:
- **savage**: Brutally honest but caring (default)
- **supportive**: Encouraging and understanding
- **neutral**: Balanced and factual
- **chaos**: Unhinged and unpredictable

### Automated Scripts

Set up cron jobs for automated features:

**Daily Check-Ins** (check for inactive users):
```bash
0 10 * * * cd /path/to/RCSClutchIt && source venv/bin/activate && python check_inactive_users.py
```

**Weekly Summaries** (send on Sundays):
```bash
0 9 * * 0 cd /path/to/RCSClutchIt && source venv/bin/activate && python send_weekly_summaries.py
```

## 🔒 Security

- **Data Isolation**: Each user's data is completely separate
- **Prompt Injection Protection**: Guardrails prevent prompt manipulation
- **Rate Limiting**: Prevents abuse with message frequency limits
- **Anti-Hallucination**: All calculations done in code, not GPT
- **User Preferences**: Respects all opt-out requests

## 🧪 Testing

Test database connection:
```bash
python test_db_connection.py
```

Test Twilio connection:
```bash
python test_twilio_connection.py
```

Check database status:
```bash
python check_db_status.py
```

## 📚 Documentation

- `COMPLETE_FEATURE_LIST.md` - Full feature list
- `CONTEXT_AWARENESS_UPDATE.md` - Context awareness & budget tracking
- `BUDGET_CATEGORY_UPDATE.md` - Category-specific budgets
- `ANTI_HALLUCINATION.md` - Anti-hallucination safeguards
- `SECURITY.md` - Security measures
- `DATA_ISOLATION.md` - Data isolation details

## 🤝 Contributing

This is a private repository. For questions or issues, contact the repository owner.

## 📝 License

Private - All rights reserved

## 🙏 Acknowledgments

Built with:
- [FastAPI](https://fastapi.tiangolo.com/)
- [OpenAI GPT](https://openai.com/)
- [Twilio](https://www.twilio.com/)
- [Supabase](https://supabase.com/)

---

**Made with 💰 and a lot of coffee ☕**
