### Deliverable 1: Written Problem and Solution Statement

# WellWork: AI-Powered Workplace Wellness

**Problem**: High-pressure workplaces like call centers, retail, and startups, especially in South India, expose employees to stress and burnout, leading to disengagement, low productivity, and high turnover. This undermines SDG 8’s goals of safe work environments and productive employment (8.8, 8.5). SMEs, critical for economic growth (8.3), lack affordable, tailored wellness solutions to support workers in repetitive roles. Generic wellness apps are disconnected from workplace contexts, failing to engage employees or integrate self-care into busy schedules, leaving workers feeling unsupported.

**Solution**: **WellWork**, powered by IBM Granite models, is an AI-driven platform that acts as a personalized wellness coach to reduce stress and enhance engagement. Targeting SME employees, HR teams, and owners, it analyzes schedules, task loads, and self-reported mood (via quick app surveys) to deliver tailored wellness activities (e.g., 5-minute mindfulness exercises, stretch breaks, motivational quotes) during downtime. Employees access a mobile/web app, earning points and completing gamified challenges (e.g., “Daily Calm Quest”) to make self-care fun. Managers use a dashboard to monitor wellness trends, ensuring supportive environments. Granite’s NLP crafts context-aware, culturally sensitive prompts, enhancing accessibility in diverse regions.

**Interaction**: Employees log in, answer brief mood surveys (e.g., “Feeling stressed?”), and receive personalized wellness suggestions. They complete activities, track points, and join team challenges. Managers gain insights to adjust workloads or promote wellness initiatives. Multilingual support (e.g., Tamil, Kannada) ensures inclusivity.

**Creativity and Uniqueness**: Unlike generic wellness apps, WellWork embeds AI-driven, context-aware interventions into workflows, delivering short, engaging activities tailored to workplace realities. Its gamified, culturally relevant approach engages underserved workers, transforming downtime into rejuvenating moments. This novel integration of wellness into daily work sets a new standard for SME employee care.

**Impact**: WellWork fosters safe, healthy workplaces (SDG 8.8) by reducing burnout, boosting productivity (8.5), and improving retention, enabling SMEs to scale (8.3). Its scalable, inclusive design offers judges a fresh AI solution that redefines workplace wellness, empowering workers in high-pressure roles with engaging, accessible self-care.



---

### Deliverable 2: Written Statement on IBM Granite Usage

# IBM Granite Usage in WellWork

**WellWork** harnesses IBM Granite models via Watsonx to deliver AI-driven workplace wellness, reducing stress and supporting SDG 8. Granite’s advanced natural language processing (NLP) powers personalized, context-aware wellness interventions for SME employees, making self-care engaging and accessible.

1. **Personalized Wellness Recommendations**: Granite’s text analysis processes employee data (e.g., schedules, task loads, mood surveys) to generate tailored wellness activities (e.g., “Try a 5-minute breathing exercise, Priya”). Recommendations adapt to workload and stress levels, ensuring relevance.

2. **Gamified Prompts**: Granite’s text generation crafts motivational, culturally sensitive prompts for wellness challenges (e.g., “Join the Daily Calm Quest in Tamil!”), integrating gamification to make activities fun and encouraging participation in busy workplaces.

3. **Conversational Coaching**: Granite’s chatbot capabilities provide real-time support, responding to employee inputs (e.g., “I’m stressed”) with empathetic guidance (e.g., “Let’s try a quick stretch”). This conversational approach keeps wellness interactive and supportive.

4. **Wellness Insights**: Granite analyzes mood and engagement data to provide managers with actionable insights (e.g., identifying high-stress teams), promoting equitable wellness support (SDG 8.8).

5. **Multilingual and Ethical AI**: Granite’s multilingual support (e.g., Tamil, Kannada, Hindi) ensures accessibility for diverse workforces, particularly in South India. Its bias mitigation guarantees fair recommendations, and anonymized data protects privacy.

By leveraging Granite, WellWork transforms workplace wellness into a dynamic, inclusive experience, reducing burnout and enhancing productivity. Its AI-driven personalization and gamification offer a unique approach to fostering safe, healthy work environments and SME growth.



---

### Deliverable 3: Working Code Repository or Evidence of Technology Proof-of-Concept (Optional)

#### PoC Approach
- **Objective**: Showcase WellWork’s core features: AI-driven wellness recommendations, gamified challenges, and manager insights, powered by Granite.
- **Scope**: Build a minimal web app with:
  - **Employee View**: Mood survey, personalized wellness activities, points tracking.
  - **Manager View**: Dashboard with wellness metrics (e.g., stress levels, activity completion).
  - **AI Integration**: Granite-generated prompts based on fake employee data.
- **Tech Stack** (per React/JSX guidelines):
  - **Frontend**: React.js (CDN-hosted via cdn.jsdelivr.net).
  - **Backend**: Python (Flask) for Watsonx API calls.
  - **AI**: Watsonx APIs for Granite (text generation, analysis).
  - **Styling**: Tailwind CSS for an accessible, autism-friendly UI (soft colors, clear layouts, per your social story interest).
  - **Hosting**: Vercel or IBM Cloud.
  - **Data**: Fake employee and wellness data.

#### Fake Data for WellWork
This CSV simulates employee profiles, schedules, and mood data for wellness recommendations. 10 records for brevity, expandable to 20:

```csv
EmployeeID,Name,JobRole,Department,TaskLoad,ShiftHours,MoodScore,PreferredLanguage,WellnessActivityCount,EngagementScore
E001,Arun Nair,Retail Associate,Sales,High,8,60,Malayalam,2,75
E002,Priya Sharma,Customer Service Rep,Support,Very High,10,50,Tamil,3,80
E003,Vikram Patel,Inventory Clerk,Logistics,Medium,7,70,Gujarati,1,70
E004,Lakshmi Rao,Cashier,Sales,High,8,65,Kannada,2,78
E005,Rahul Menon,Call Center Agent,Support,Very High,9,55,Malayalam,4,85
E006,Anjali Desai,Retail Associate,Sales,Medium,8,68,Hindi,3,77
E007,Suresh Kumar,Warehouse Worker,Logistics,High,10,62,Tamil,1,72
E008,Meera Iyer,Customer Service Rep,Support,Very High,9,58,Kannada,3,81
E009,Amit Shah,Cashier,Sales,Low,7,72,Gujarati,2,74
E010,Divya Suresh,Inventory Clerk,Logistics,Medium,8,67,Malayalam,2,76
```

**Notes**:  
- **Columns**: Include wellness-relevant fields (TaskLoad, ShiftHours, MoodScore) and regional context (PreferredLanguage). MoodScore (0–100) reflects self-reported stress (lower = more stressed).  
- **Use**: Feed into Granite to generate activities (e.g., “Priya, try a 5-minute mindfulness break in Tamil”).  
- **Export**: Save as `wellwork_data.csv` for Grafana integration or Python processing.

#### PoC Steps
1. **Set Up Watsonx**:
   - Access Watsonx (https://www.ibm.com/products/watsonx).
   - Get API keys for Granite (e.g., granite-13b-chat).
   - Test prompt:
     ```python
     prompt = "Generate a 5-minute wellness activity for Priya Sharma, a Customer Service Rep with a Very High task load and MoodScore of 50. Use Tamil and a motivational tone."
     ```

2. **Build Frontend**:
   - Create a React app with:
     - **Mood Survey**: Form with sliders (e.g., “How stressed are you? 0–100”).
     - **Wellness Page**: Display AI-generated activities and points.
     - **Manager Dashboard**: Table of MoodScores and ActivityCounts.
   - Example JSX:
     ```jsx
     import React, { useState, useEffect } from 'react';
     const App = () => {
       const [activities, setActivities] = useState([]);
       useEffect(() => {
         fetch('/api/wellness?employeeID=E002')
           .then(res => res.json())
           .then(data => setActivities(data));
       }, []);
       return (
         <div className="p-4 bg-blue-100 min-h-screen">
           <h1 className="text-2xl font-bold">WellWork</h1>
           {activities.map(activity => (
             <div className="bg-white p-3 m-2 rounded shadow" key={activity.id}>
               {activity.text}
             </div>
           ))}
         </div>
       );
     };
     export default App;
     ```

3. **Build Backend**:
   - Use Flask to process CSV and call Watsonx:
     ```python
     from flask import Flask, request
     import pandas as pd
     import requests
     app = Flask(__name__)
     WATSONX_API_KEY = "your_api_key"
     WATSONX_URL = "https://api.watsonx.ai/v1/generate"
     data = pd.read_csv("wellwork_data.csv")
     @app.route('/api/wellness')
     def get_wellness():
         employee_id = request.args.get('employeeID')
         employee = data[data['EmployeeID'] == employee_id].iloc[0]
         prompt = f"Generate a 5-minute wellness activity for {employee['Name']}, a {employee['JobRole']} with {employee['TaskLoad']} task load and MoodScore of {employee['MoodScore']}. Use {employee['PreferredLanguage']} and a motivational tone."
         headers = {"Authorization": f"Bearer {WATSONX_API_KEY}", "Content-Type": "application/json"}
         payload = {"model": "ibm/granite-13b-chat", "prompt": prompt, "max_tokens": 150}
         response = requests.post(WATSONX_URL, json=payload, headers=headers)
         return response.json().get("generated_text", "")
     if __name__ == '__main__':
         app.run(debug=True)
     ```

4. **Host and Share**:
   - Push to GitHub (e.g., `github.com/yourusername/wellwork-poc`).
   - Deploy on Vercel or IBM Cloud.
   - README:
     - Project overview, SDG 8 alignment.
     - Setup (e.g., `pip install flask pandas requests`).
     - Screenshots (survey, activities, dashboard).
     - Demo link.

5. **Alternative Evidence**:
   - **Canva Mockups**: Create UI mockups:
     - **Page 1**: Mood survey form (sliders, buttons).
     - **Page 2**: Wellness activity card with points.
     - **Page 3**: Manager dashboard with table.
     - Steps: Search “cartoon survey” in Canva, use blue/white palette, export as PNG.
   - **Video Demo**: 1–2 minute video showing mockups or API outputs.
   - **API Results**: Run Granite prompts in Jupyter, save outputs (e.g., wellness activities), share as PDF.

#### Repository Structure
```
wellwork-poc/
├── public/
│   ├── index.html
│   └── styles.css (Tailwind CSS)
├── src/
│   ├── App.js (React components)
│   └── api.js (API calls)
├── server/
│   ├── server.py (Flask backend)
│   ├── wellwork_data.csv
│   └── requirements.txt
├── README.md
└── screenshots/
    ├── mood_survey.png
    ├── wellness_activity.png
    ├── manager_dashboard.png
```

---
