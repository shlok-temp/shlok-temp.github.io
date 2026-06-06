---
layout: post
title: "Markets & Forecasting: How my passion lead to Google-backed KaggleX fellowship"
date: 2023-12-05
categories: [Data-Science, Machine-Learning]
tags: [python, xgboost, time-series, ml]
image: /assets/images/forecasting-banner.jpg
description: "How my passion for markets led to a Google-backed KaggleX Fellowship, and the hybrid time-series and gradient boosting architecture I built to achieve 87.8% accuracy."
---

![Forecasting Feature Image]({{ site.baseurl }}/assets/img/ban2.jpeg)

In the summer of 2023, my deep-rooted passion for financial markets naturally drew me into the complex world of time-series forecasting. I started spending countless hours working on predictive models, fascinated by the idea of decoding hidden patterns within seemingly chaotic datasets. It was during this intense period of self-directed research and building that I decided to apply for the KaggleX BIPOC Fellowship. 

I had actually applied to the previous cohort and faced a tough rejection. So, when the acceptance email finally arrived this time around, my excitement went through the roof. Based on the rigorous preliminary forecasting work I had been doing and the technical requirements of my ongoing projects, I was officially allotted the fellowship and awarded the prestigious $1,000 KaggleX Scholarship, backed by Google. 

This program wasn't merely an academic exercise; it was an intensive, mentorship-driven deep dive. Paired with an incredible mentor, Ayon Roy, I had the perfect environment to tackle a notoriously difficult challenge: mastering complex store sales forecasting.

---

## The Problem: The Chaos of Retail Data

Forecasting retail sales is a problem that sits at the volatile intersection of human behavior, macroeconomics, and temporal cycles. Unlike stationary datasets where patterns remain relatively consistent over time, store sales data is inherently chaotic. It is heavily influenced by overlapping seasonal trends, sudden holiday sales spikes, localized promotional events, and random economic noise. 

When I first began analyzing the historical data, it became immediately apparent that relying on a singular, standard machine learning algorithm would be insufficient. A simple linear regression model would completely miss the overarching macro-trends, while a basic tree-based model might overfit to the random noise, failing to generalize to future data points. To achieve elite predictive performance, I needed to push the boundaries of standard modeling and engineer a highly sophisticated, multi-layered solution.

---

## The Architecture: A Hybrid Paradigm

The core philosophy driving my approach was the understanding that different machine learning algorithms possess distinctly different strengths. I spent several weeks conceptualizing a hybrid forecasting architecture that could leverage the unique advantages of two entirely distinct paradigms: classical time-series decomposition and modern gradient boosting. 

The goal was to create a system where one model handled the broad, predictable strokes of the data, while a second model aggressively targeted the unpredictable, non-linear anomalies left behind.

### Layer 1: Capturing the Macro with Prophet
For the foundation, I turned to `Prophet`, a robust forecasting procedure built for handling time-series data that displays strong seasonal effects and historical trend changes. I engineered the Python pipeline to utilize `Prophet` to capture the macro-level trends. 

This involved carefully tuning the model to recognize multi-period seasonality, explicitly mapping out weekly shopping habits, monthly wage cycles, and yearly holiday patterns. By configuring `Prophet` to understand these underlying rhythms, I generated a baseline forecast—a highly accurate representation of what sales should look like in a perfectly predictable world.

### Layer 2: Conquering the Residue with XGBoost
The real world, however, is never perfectly predictable. `Prophet` inherently struggles with sharp, sudden irregularities that occur in daily operations. This is where the second layer of the hybrid architecture was introduced. 

I engineered the pipeline to isolate the statistical *residue* of the `Prophet` model—the exact mathematical difference between the smooth baseline prediction and the actual historical sales data. This residue represented everything the time-series model failed to understand: the chaotic noise, the impact of a sudden local competitor, or the unexpected success of a specific product promotion. 

To conquer this residue, I deployed an `XGBoost Regressor`. Instead of training the XGBoost model on the raw sales figures, I trained it explicitly to learn and fit onto the error margin left behind by the first model. The algorithm essentially learned how to predict the mistakes of the Prophet baseline based on auxiliary features like daily oil prices, specific holiday flags, and localized promotional data.

---

## The Engineering Sprint and Final Results

The engineering required to make these two systems work in tandem was the most demanding phase of the fellowship. I spent over a month writing Python scripts to iteratively tune the hyperparameters of both models simultaneously, ensuring they complemented rather than contradicted one another. I built robust data cleaning pipelines to handle missing values without breaking the strict chronological order required for time-series forecasting, and I implemented complex time-series cross-validation techniques to ensure the model was never inadvertently exposed to future data.

By layering the immense gradient-boosting power of XGBoost directly on top of Prophet’s seasonal baseline, I successfully created a framework that could see both the forest and the trees. It respected the overarching, macro-economic seasonal cycles while aggressively adapting to daily, micro-level anomalies. 

When deployed against a complex, unseen testing dataset, **the final hybrid model achieved an outstanding 87.8% predictive accuracy.**

Beyond the raw metrics, the KaggleX Fellowship was a profound period of professional growth. Weekly touchpoints with my mentor forced me to constantly defend my architectural decisions, refine my code quality, and think about scalability. Collaborating with a global cohort of peers completely transformed my confidence as an engineer. It taught me that true engineering is about deeply understanding the underlying physics of your data, embracing its chaos, and orchestrating highly customized, complementary systems to win.



*I use AI for proof-reading & grammar*