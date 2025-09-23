## Executive summary

We’re building **FinEd AI** — an AI-powered **Financial Literacy Coach**: it teaches budgeting, saving, debt management, and investing basics through interactive lessons, gamified challenges, and an AI chatbot coach. Core UX: a user signs in or enters guest mode, inputs income/expenses or uses a demo budget, and gets personalized recommendations, simulations, and educational modules.

## MVP (must-have) in one line

Budget input → AI-generated financial profile → Personalized savings/expense recommendations → Gemini AI chatbot coach → Gamified challenges.

## Why this exact product?

- Tackles **financial illiteracy**, a root cause of poverty & debt.  
- AI + gamification ensures **engagement and measurable learning**.  
- Demo is intuitive: user inputs income/expenses → gets advice instantly.  
- Strong portfolio value: FinTech + AI + data privacy = employer appeal.

## Personas

- **Young adult (Student/Worker)** — wants to learn budgeting & saving.  
- **Parent** — seeks guidance on long-term planning.  
- **Educator** — integrates financial literacy in workshops.  
- **Admin/Demoer** — seeds sample budgets, tracks demo analytics.

---

## Full list of user stories

#### Onboarding & accounts

1. **Guest demo (P1)**  
   - As a User, I want to try the app without signing up.  
   - AC: demo profile created.

2. **Signup/login (P2)**  
   - As a User, I want secure login so my data is private.  
   - AC: JWT or Google OAuth.

#### Budgeting & simulation

3. **Input budget (P1)**  
   - As a User, I want to input income & expenses so AI can analyze them.  
   - AC: form saves categories.

4. **Expense analyzer (P1)**  
   - As a User, I want the AI to highlight risky spending.  
   - AC: Gemini identifies overspending categories.

5. **Savings goal (P1)**  
   - As a User, I want to set a goal and see a savings plan.  
   - AC: plan includes timeline & suggestions.

6. **Scenario simulator (P1)**  
   - As a User, I want to simulate “what if” scenarios.  
   - AC: AI shows outcome of changing expenses/income.

#### Education & gamification

7. **Micro-lessons (P1)**  
   - As a User, I want to learn small financial lessons.  
   - AC: 5–10 min modules.

8. **Gemini AI chatbot (P1)**  
   - As a User, I want to ask finance questions in plain language.  
   - AC: Gemini responds with explanations.

9. **Gamified challenges (P2)**  
   - As a User, I want to complete challenges (e.g., “Save 5% this week”).  
   - AC: points/badges awarded.

#### Tracking

10. **Dashboard (P1)**  
   - As a User, I want to see goals, spending trends, and progress.  
   - AC: charts + summaries.

---

## Acceptance criteria summary

- User can enter a budget and receive personalized advice.  
- AI chatbot answers at least 3–5 questions.  
- Savings goal & scenario simulator functional.  
- Dashboard tracks spending trends.  

---

## Tech stack

- **Frontend:** HTML5, CSS3, JS (responsive financial dashboard).  
- **Backend:** Node.js + Express.js.  
- **Database:** Supabase/PostgreSQL (user budgets, lessons, challenges).  
- **AI:** Gemini AI for chatbot & financial analysis.  
- **Auth/Security:** JWT, Google OAuth, bcrypt for passwords.  
- **Cloud:** Azure hosting + GitHub CI/CD.

---

## Architecture

1. Frontend (finance dashboard).  
2. API Gateway (Express.js).  
3. Budget Analyzer Service (rules + Gemini insights).  
4. Learning Engine (modules, challenges).  
5. Supabase/Postgres for persistence.  

---

## Data & schema

**Users table**: id, name, email, hashed_pw, profile_json.  
**Budgets table**: user_id, income, expenses_json, timestamp.  
**Goals table**: user_id, goal_type, target_amount, target_date.  
**Lessons table**: id, title, topic, difficulty, content_url.  
**Challenges table**: id, title, points, status.

---

## ML & logic plan

- **Budget analyzer:** Rules (50/30/20 rule) + Gemini explanation.  
- **Scenario simulator:** Adjust income/expenses → recompute savings timeline.  
- **AI tutor:** Gemini answers “What is compound interest?” etc.  
- **Gamification:** Points per lesson/challenge, stored in DB.

---

## API spec

- POST /api/budget/submit → stores budget, returns analysis.  
- GET /api/goals/:user_id → returns goals.  
- POST /api/goals/set → sets savings goal.  
- POST /api/simulate → runs scenario.  
- POST /api/ask-ai → forwards to Gemini.  

---

## Frontend UX & pages

- Landing: “Get smarter with money”.  
- Budget input form.  
- Dashboard (expenses, goals, trends).  
- Lessons page (micro-courses).  
- Chatbot modal (Gemini).  
- Challenges page (badges).  

---

## Backend MVP

- Budget input + analyzer.  
- Gemini AI integration for expense feedback.  
- Savings goal endpoint.  
- Dashboard data aggregator.  

---

## Polish & reliability

- Encrypt stored budgets.  
- Privacy disclaimer.  
- Export option: PDF report of budget plan.  

---

## Testing & metrics

- Unit test budget analyzer.  
- API contract tests.  
- Metrics: % users hitting savings goals, lesson completion rates.  

---

## Data sourcing & seeding

- Seed 20 demo budgets (low, medium, high income).  
- Seed lessons (budgeting basics, debt traps, saving strategies).  
- Seed 5–10 challenges.

---

## Security & ethics checklist

- Use bcrypt for password hashing.  
- Clear disclaimers: “Educational only, not financial advice.”  
- Encrypt sensitive user financial data.  

---

## README template (sections)

- Project name + tagline.  
- Demo screenshots.  
- Quickstart (run backend/frontend).  
- Architecture overview.  
- Data sources & licenses.  
- Ethics statement.  
- Roadmap.  

---

## Pitch/demo guide

1. Landing → guest demo.  
2. Input budget → instant AI insights.  
3. Set savings goal → see plan.  
4. Ask Gemini chatbot a question.  
5. Show progress dashboard & gamification.  
6. Wrap: “With FinEd AI, anyone can learn to manage money.”
