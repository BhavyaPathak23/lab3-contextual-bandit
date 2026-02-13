# Lab 3 - Contextual Bandit-Based News Article Recommendation System

## Student Information
- **Name:** Bhavya Pathak
- **Roll Number:** U20230136
- **Course:** Reinforcement Learning Fundamentals
- **Assignment:** Lab 3 - Contextual Multi-Armed Bandits

---

# Student Submission Checklist

## Repository and Branching
- [x] Repository created correctly on GitHub
- [x] All work committed to single branch: BhavyaPathak_U20230136
- [x] No work pushed to master branch
- [x] Correct branch pushed to GitHub

## Notebook Submission
- [x] Exactly one notebook submitted
- [x] Notebook placed at repository root
- [x] Notebook named correctly: lab3_results_U20230136.ipynb
- [x] Notebook runs top-to-bottom without errors
- [x] All outputs and plots visible

## Sampler Usage
- [x] rlcmab-sampler used without modification
- [x] Sampler initialized using roll number 136
- [x] Rewards obtained only via sampler.sample(j)
- [x] No synthetic rewards used

## Contextual Bandit Implementation
- [x] User category used as context
- [x] News category used as arm
- [x] Correct arm index mapping followed
- [x] Implemented Epsilon-Greedy, UCB, and SoftMax

## Evaluation and Plots
- [x] Classification accuracy reported
- [x] RL simulation run for T = 10,000
- [x] Average Reward vs Time plots included
- [x] Hyperparameter comparison plots included
- [x] All plots labeled with titles and legends

---

# 1. Project Overview

This project implements a Contextual Multi-Armed Bandit (CMAB) based News Recommendation System.

Goal:
- Predict user category using a classification model
- Use contextual bandit algorithms to select optimal news category
- Recommend a news article that maximizes engagement reward

Contexts = User Categories  
Arms = News Categories

---

# 2. Problem Formulation

## Contexts
- User1
- User2
- User3

## Arms
- Entertainment
- Education
- Tech
- Crime

Total Arms = 12

Arm Mapping:
- 0–3 → User1
- 4–7 → User2
- 8–11 → User3

---

# 3. Dataset Description

## User Data
- train_users.csv
- test_users.csv
Used for user classification and context detection.

## News Dataset
- news_articles.csv
Contains categorized news articles.

## Reward Sampler
Used rlcmab-sampler package.

Rewards were obtained strictly using:
reward = reward_sampler.sample(j)

No synthetic or manually generated rewards were used.


---

# 4. System Design and Implementation

## 4.1 Data Preprocessing
- Loaded datasets
- Cleaned missing values
- Encoded categorical variables
- Prepared features for model training

---

## 4.2 User Classification
- Dataset split: 80% train / 20% validation
- Model trained to predict User1/User2/User3
- Evaluated using classification_report

Validation Accuracy: **[91.5%]**

Classifier serves as Context Detector.

---

## 4.3 Contextual Bandit Algorithms

Separate policies trained for each context.

### Epsilon-Greedy
Tested epsilon values:
- 0.05
- 0.1
- 0.2

### Upper Confidence Bound (UCB)
Tested exploration constants:
- 0.5
- 1
- 2

### SoftMax
- Temperature τ = 1

---

## 4.4 Reinforcement Learning Simulation
- Time Horizon T = 10,000
- Expected rewards calculated
- Policies learned per context

---

## 4.5 Recommendation Engine Workflow

1. Predict user category
2. Select optimal news category
3. Randomly sample article from news dataset
4. Output context, category, and article

---

# 5. Results and Observations

## Classification Performance
- Model successfully classified users into correct contexts

## RL Learning Behavior
- Reward increased over time
- Policies converged during simulation

## Hyperparameter Insights
- Moderate exploration gave stable results
- UCB handled exploration efficiently
- SoftMax showed smooth learning patterns

## Algorithm Comparison
| Algorithm | Observation |
|----------|-------------|
| Epsilon-Greedy | Stable with tuned epsilon |
| UCB | Efficient exploration |
| SoftMax | Smooth convergence |

---

# 6. Plots Included
- Average Reward vs Time (per context)
- Epsilon Hyperparameter Comparison
- UCB Hyperparameter Comparison

All plots include:
- Titles
- Axis labels
- Legends

---

# 7. How to Reproduce the Experiments

## Install Dependency
pip install rlcmab-sampler

## Run Notebook
Open the notebook:
lab3_results_U20230136.ipynb

Run all cells sequentially from top to bottom.

## Expected Outputs
- Classification performance metrics
- Contextual bandit training
- Reward learning curves
- Hyperparameter comparison plots
- News article recommendations

---

# 8. Design Decisions
- Context derived from classification model
- Separate bandit models per context
- Hyperparameter tuning included
- Article recommendation via category filtering

---

# 9. External References
- Scikit-learn Documentation
- Lab Handout
- Lecture Notes - Reinforcement Learning Fundamentals Course

---

# 10. Conclusion

This CMAB system integrates classification with reinforcement learning to produce personalized news recommendations.

Findings:
- UCB achieved strong exploration
- Epsilon-Greedy performed consistently
- SoftMax produced smooth reward improvement

The final system successfully recommends news articles tailored to user context.

---
