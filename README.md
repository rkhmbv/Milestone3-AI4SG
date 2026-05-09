# Milestone3-AI4SG

**1. Problem — Who is affected, and what specifically breaks down for them today?**
  
Clean water and sanitation in San Jose are severely impacted by both environmental and infrastructure challenges. Over 1,000 residents living in encampments along waterways contribute significant amounts of biowaste and trash, increasing bacteria levels in local creeks and the Bay, while storm drains carry hazardous chemicals directly into these waterways. One person affected could be an unhoused resident living near a creek who relies on nearby water sources for daily needs, despite contamination risks that can lead to serious health issues. The most critical failure point in this system is the city’s aging infrastructure and pressure instability, which allow contamination, sediment release, and inconsistent water quality even after treatment, leaving vulnerable individuals with no reliable access to safe, clean water.

**2. AI Capability — Which lab capability addresses the failure point, and why does it fit?**

The failure point is addressed by Lab 2, where the AI capability of structured output generation using schema-constrained prompting. This capability fits because the main problem was inconsistency. The original prompt only asked the AI to “Extract water issue info,” so the model responded with free-form natural language instead of structured data. As a result, the output was vague, inconsistent, and difficult for software systems to parse automatically. The code expected specific fields such as location, issue type, contaminants observed, urgency, and department, but instead received a paragraph of text, which could break the automated pipeline. By introducing a strict schema prompt that forces the model to return valid JSON with predefined fields, the AI produces predictable and machine-readable outputs every time. This makes the system reliable for automated processing because each response follows the same structure and can be directly integrated into the City of San Jose Environmental Services workflow without errors.

**3. Workflow — What goes in, what does the AI do, what comes out, and who acts on the output? Include screenshots of output**

Input: Real-time data from IoT water sensors (pH, bacteria levels, turbidity, chemical presence) placed in creeks, storm drains, and pipelines Weather and runoff data (rainfall, flooding risk) Reports from community members (mobile app or SMS alerts) Uploaded images from users (e.g., photos of water color, trash buildup, pipe leaks) analyzed via image recognition Historical infrastructure and maintenance records

AI Processing: Machine learning models detect anomalies in water quality and pressure levels Computer vision analyzes uploaded images to identify pollution indicators (e.g., discoloration, visible waste, oil sheen, pipe damage) Predict contamination spikes based on weather patterns and usage trends Identify high-risk zones (e.g., encampments near waterways or weak infrastructure points) Prioritize areas needing urgent intervention

Output: Real-time alerts to city agencies and public dashboards Risk maps showing contaminated or unsafe water zones Flagged image reports with severity levels and location tagging Automated recommendations (e.g., flush pipelines, deploy cleanup crews, distribute water supplies)

Real-World Action: City officials respond quickly to contamination events Targeted infrastructure repairs and maintenance NGOs and outreach teams distribute clean water to unhoused populations in high-risk areas Community members actively contribute by reporting visible issues through images Long-term planning informed by predictive insights to prevent recurring issues

In this system, we use a predefined schema as part of the AI’s instructions so that every response follows the same structured JSON format. This guarantees consistency and makes the data predictable and easy to use. For example, no matter how a resident describes an issue such as reporting a chemical smell near a storm drain, the AI will always return standardized fields like "location", "issue_type", and "urgency". This consistency is critical because it allows the system to automatically process and act on the data without needing manual interpretation. It enables: Automated database entry into systems like 311 or custom water quality platforms Reliable machine learning input using clean and structured data Efficient dispatching by identifying the correct department (e.g., Environmental Services) Reduced human error and faster response times Overall, structured, machine-readable output transforms raw resident complaints into actionable insights for the City of San Jose.

<img width="1084" height="586" alt="Screenshot 2026-05-09 at 2 06 19 PM" src="https://github.com/user-attachments/assets/a473bd4c-36b1-43a2-b457-95d09409e16f" />

<img width="578" height="260" alt="Screenshot 2026-05-09 at 2 07 32 PM" src="https://github.com/user-attachments/assets/d48baed7-2b38-4b32-a8da-553e45efeddc" />

**4. Failure Case — One specific failure, with a reference to the lab output that showed it is possible.**

Prompt: "Extract water issue info."
Output: "There's dirty water and trash near a creek on Elm Street. This appears to be a water contamination issue with possible waste pollutants. The situation may require attention due to potential health risks."
Assessment: Failure - the output is too vague, unstructured text and cannot be reliably parsed into JSON for automated processing. The code expects structured data, but gets a paragraph instead, so it breaks.
<img width="850" height="446" alt="Screenshot 2026-05-09 at 2 18 55 PM" src="https://github.com/user-attachments/assets/17f3f671-c638-4efb-aa39-3ff2fc65f455" />

**5. Oversight and Tradeoff**

Oversight decision: People should review all AI-generated reports labeled as “HIGH” or “CRITICAL” urgency before they are forwarded to the City of San Jose Environmental Services Department. This oversight helps prevent incorrect classifications, false alarms, or missed public safety risks caused by inaccurate AI outputs. Tradeoff: Adding human review increases response time and requires more staff resources, which can reduce the speed and efficiency of the automated system.
One change: The system should use schema-constrained prompting so the AI always returns structured JSON output instead of free-form text. This would improve reliability because the extracted information could be parsed automatically into the city’s processing pipeline without errors. Tradeoff: Strict schemas reduce flexibility, meaning unusual or unexpected reports may lose important contextual details that do not fit the predefined fields.
