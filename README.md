## Ousia
By: Danny Whitaker

**Status:** Completed
**Accuracy:** With ROUGE-1: 0.53. With ROUGE-L: 0.42.
**Impact:** $7.0m+ USD Annual Savings

# Executive Summary
This capstone project was designed to address the critical information overload problem on modern messaging platforms. By implementing and fine-tuning a BART transformer model and comparing its results with those of a GPT-2 model on the same SAMSum dataset, we created a production-ready summarization engine capable of accurately condensing long conversational threads into short summaries.

# Results

**Performance:** I was able to achieve 0.53 ROUGE-1 score which exceeded my target value of 0.40. 
**Efficiency:** Reduced summarization time from 300s (human avg) to just under 1s (0.83s) using the AI model.
**Value Created:** I was able to create a small business dashboard that projected that the operational savings would be ~$7.6 million/year if deployed in a large scale at help desks, and call centers.

# Project Statement
Many messaging flatforms (Slack, MS Teams, WhatsApp, Discord, and Instagram Messages) suffer from high noise-to-signal ratio.
**Average Catch-up time:** The average user takes roughly 5-8 minutes to catch up to present time per thread they read.
**User Frustration:** There is high drop-off rates in high-vol groups.
**Manual Cost:** Customer support agents, and call center support agents spend roughly ~20% of their time reading context before supporting people in need. This model allows support agents to be able to understand the issue within seconds so that they can get on to trying to solve said issue.

**My Solution:** Create an automated, privacy-preserving (local) AI summarizer that generates instant briefs for users, allowing for the user to catchup and understand the context within seconds.

# Technical Approach
**Model Architecture:**
In this project we compared the results of BART and GPT-2, and came to the conclusion that BART was more applicable for this scenario.
*Why Bart?* Unlike GPT-2, BART is able to read the entire input sequence before generating text. This makes it better for summarization and ensures that it doesnt hallucinate.
**Comparisonm:** We benchmarked BART against GPT-2 and found that GPT failed to generate a single accurate summary.

**Data Pipeline**
**Dataset:** For this dataset, I decided to implement SAMSum Corpus. I imported it directly to the file for ease of use.
**Preprocessing:** I created a pretty standard tokenization pipeline using 'facebook/bart-large-cnn' tokenizer.
**Optimization:** Strategic dataset slicing allowed us to save time in processing the data so that we could quickly alter and fine-tune iterations.

**Tracking Strat**


# Results & Eval
**How did we evaluate the model?** We utilized the ROUGE (Recall-Oriented Understudy for Histing Eval) test and compares its scores against human written refrences.

Rouge-1 : 0.52 : > 0.4
Rouge-2 : 0.27 : > 0.2
Rouge-L : 0.41 : > 0.4

**Qualitative Analysis**
**Strengths:** The model was able to capture core intents of the conversation. This includes places, times, decisions, and more with high fidelity.
**Weaknesses:** There was times where I found that there would be a "Speaker Attribution Error". This means that it would fail to get the right people correctly. In our testing, it confused Kim for Claire in a multi-party thread about food.

# Business Impact

In this same file, I modeled the ROI based on the deployment of 10,000 threads a day.

Heres what I found:
**Human Labor Cost:** $20,833 / Day (assuming that each is paid at ~$25/hour)
**AI Compute Cost:** #1.38 / Day (this is with googles T4 GPU)
**Efficiency Gain:** This means that deploying the model is a little more than 15000x more affordable than manual huamn summarization, and it saves time for the people at the support desk.
**Privacy:** Because its local, it could be considered to be very secure.

# Future Implements & Work
1. Fix Speaker Attribution Errors
2. Deployment using Docker and a FastAPI
3. Feedback Loop to help with future reinforced learning.

# How to Run
1. Install required Dependencies
  '''bash
  pip install -r requirements.txt
3. Run!

