Project Title
"Forecasting Dengue Resurgence in Asia: A Cross-Regional Comparison of Machine Learning and Compartmental Models Across Thailand, Sri Lanka, and Bangladesh"

Problem Statement
Dengue fever kills thousands every year across Asia. Governments need to know when the next big outbreak is coming so they can prepare hospitals, deploy mosquito control teams, and warn the public in time.
Two types of models exist to forecast this:
Model 1 — SARIMA (Machine Learning)
This model looks at past dengue case numbers and finds patterns. If dengue peaked every July for the last 10 years, it assumes July will be bad again next year. It is purely based on history — it has no idea why dengue spreads, it just sees that it did.
Model 2 — SEIR-Vector (Mechanistic)
This model understands the biology. It tracks how many people are currently susceptible, how many are infected, how mosquito populations change with seasons, and how immunity builds up in a population after an outbreak. It knows that after a quiet year, more people are susceptible — meaning the next outbreak could be bigger than history suggests.
The Problem:
Both models can look accurate when tested on past data. But they can give completely opposite predictions about the future — especially after an unusually quiet year. A policymaker looking at the ML model might think everything is fine and do nothing. The mechanistic model might be screaming that a big outbreak is coming. Who should they listen to?
This gets even more complicated because Thailand, Sri Lanka, and Bangladesh are very different countries — different population sizes, different levels of urbanization, different healthcare systems, different mosquito environments. A model that works well in Thailand might completely fail in Bangladesh.

Core Question

When SARIMA and SEIR-Vector models give conflicting forecasts about dengue outbreaks — which one should a public health policymaker trust, and does that answer change depending on which country they are in?


Proposed Solution
Step 1 — Get and Clean the Data

Download dengue case counts for Thailand, Sri Lanka, and Bangladesh from OpenDengue
Download population data from World Bank
Clean the data — fix missing values, convert to monthly/weekly new cases, calculate cases per 100,000 people

Step 2 — Draw Maps and Understand Spatial Differences

Draw a map showing raw case counts across the 3 countries — Bangladesh will look enormous just because it has more people
Draw another map showing cases per 100,000 people — this tells the real story
Take snapshots at different time points: early outbreak season, peak, and off-season
This section answers: are these countries really comparable? Where is dengue actually worst per person?

Step 3 — Build the SEIR-Vector Model

Build a model that simulates how dengue spreads through humans via mosquitoes
Run it separately for each country
Extract from each country: how fast does it spread (R0), how does transmission change over time (Rt), when does it peak, how high does it peak

Step 4 — Build the SARIMA Model

Build a time-series forecasting model that learns seasonal patterns from past case data
Run it separately for each country
Extract: when does it predict the peak, how high does it predict the peak

Step 5 — Compare Both Models

Build one clean comparison table showing both models side by side for all 3 countries
Peak timing, peak size, epidemic duration — do they agree or disagree?

Step 6 — Find the Disagreement

Specifically find a year that came after a quiet/low dengue season
Show that SARIMA says: "last year was quiet, next year will be moderate"
Show that SEIR-Vector says: "last year was quiet because immunity was high — now immunity has dropped, next year will be a big outbreak"
Show this with a graph where both model lines diverge
Identify which country shows the biggest disagreement — likely Sri Lanka or Bangladesh

Step 7 — Policy Argument
Answer these questions clearly:

Which model should a health minister trust when planning for next year?
Does that answer change between Thailand, Sri Lanka, and Bangladesh?
What is the real danger of a government only using the ML model?
Why does it matter that these three countries are spatially and demographically different?


Data Sources
WhatWhereHowDengue casesOpenDengueLoad directly in Python via URL — no download neededPopulationWorld BankDownload CSV from their websiteCountry mapsGeoPandas built-inOne line of code — no download needed