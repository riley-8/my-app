# Extenducation AI

**An AI-Powered, Adaptive Learning Platform for Personalized Education**

## 🎯 Executive Summary

EduBridge AI is an intelligent learning platform that diagnoses a student's knowledge gaps through a short diagnostic quiz, creates a personalized learning path, and delivers tailored micro-lessons and practice problems. The core experience involves a student taking a quiz, receiving a visual "Knowledge Graph" of their strengths and weaknesses, and being guided through a curated sequence of resources to master missing concepts, all supported by an AI explanation bot.

## 🚀 MVP (Minimum Viable Product)

**Diagnostic Quiz → Knowledge Gap Analysis → Personalized Learning Path (3-5 micro-lessons) → AI-Powered Explanation Bot (Google Gemini).**

## 👥 Target Personas

*   **The Student:** The primary user who wants to understand their weaknesses and get direct, actionable steps to improve.
*   **The Educator/Tutor:** (Future Enhancement) To track student progress and identify class-wide knowledge gaps.
*   **The Admin/Demoer:** A team member who controls demo data and scenarios for presentations.

## ✅ Core User Stories & Acceptance Criteria

| ID  | Title | User Story | Acceptance Criteria (AC) | Priority |
| :-- | :---- | :--------- | :----------------------- | :------- |
| ES1 | Take Diagnostic Quiz | As a Student, I want to take a short subject-specific diagnostic quiz so that I can identify my knowledge gaps. | Quiz is generated from a seeded bank. Answers are submitted and scored. | P1 |
| ES2 | View Knowledge Graph | As a Student, I want to see a visual "Knowledge Graph" that shows my strong and weak topics based on my diagnostic results. | UI displays a list of topics with visual proficiency scores (e.g., "Algebra: 40%"). | P1 |
| ES3 | Receive Learning Path | As a Student, I want the system to generate a prioritized list of 3-5 micro-lessons to address my biggest gaps. | For each weak topic, the system returns a title, description, and link to a resource (e.g., Khan Academy video). | P1 |
| ES4 | AI Explanation Bot | As a Student, I want to ask an AI tutor questions for further explanation on a specific problem or concept. | A chat interface allows users to ask questions. Gemini provides a contextual, educational response based on the topic. | P1 |

## 🛠️ Tech Stack

*   **Frontend:** JavaScript (ES6+), HTML5, CSS3
*   **Backend:** Node.js, Express.js
*   **Database:** Supabase (PostgreSQL)
*   **AI & NLP:** Google Gemini API
*   **Authentication:** JWT
*   **Deployment:** Microsoft Azure (App Service + Static Web Apps)
*   **Methodology:** Agile, Rapid Prototyping

## 🔍 How It Works: ML & Logic
*  1. Knowledge Gap Analysis (Rule-Based): Incorrect quiz answers are mapped to specific topics in our seeded hierarchy. A proficiency score per topic is calculated from the ratio of correct to attempted questions.
*  2.Learning Path Generation: The system identifies topics with the lowest proficiency scores and queries the resources table for the best content to address those gaps.
*  3. AI Explanation Bot (Gemini): The user's question and the relevant topic context are sent to Gemini via a carefully engineered prompt instructing it to act as a Socratic tutor, explaining concepts rather than just giving answers.

## 📊 Data Sourcing & Seeding
* **Questions:** A curated bank of 50-100 questions for a single, well-defined subject (e.g., Grade 10 Mathematics) will be created manually and stored in Supabase.
* **Resources:** A JSON file mapping each topic to 2-3 high-quality, free online resources (Khan Academy, YouTube, MDN) will be created and imported into the resources table.

  
##📈 Metrics for Impact
* **roficiency Improvement:** "After a 10-question diagnostic, a student's proficiency in 'Quadratic Equations' was 20%. After completing the recommended resources, their score on a follow-up quiz rose to 80%."
* **Engagement:** Number of completed learning paths and interactions with the AI bot.


##🔒 Security, Privacy & Ethics
* **Disclaimer:** A clear disclaimer is displayed, stating this is an educational aid and not a certified assessment tool.
* **Data:** All user quiz data is anonymized for analytics. No personally identifiable information (PII) is required for the core experience.
* **AI Safety:** Prompts to Gemini are designed to avoid generating harmful or misleading educational content.

## 🗃️ Data Schema (Supabase - Minimal)

```sql
-- Table: topics
CREATE TABLE topics (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    parent_topic_id INTEGER REFERENCES topics(id) -- for hierarchy
);

-- Table: questions
CREATE TABLE questions (
    id SERIAL PRIMARY KEY,
    topic_id INTEGER NOT NULL REFERENCES topics(id),
    question_text TEXT NOT NULL,
    correct_answer TEXT NOT NULL,
    difficulty VARCHAR(50)
);

-- Table: resources
CREATE TABLE resources (
    id SERIAL PRIMARY KEY,
    topic_id INTEGER NOT NULL REFERENCES topics(id),
    title VARCHAR(255) NOT NULL,
    url TEXT NOT NULL,
    type VARCHAR(100) -- e.g., 'video', 'article', 'exercise'
);

