# Week 1 — [Machine Learning Systems]

### 🎯 Overview
To underline the need for MLOps, we discussed the differences between prototype and production ML systems with respect to scale, data, privacy, interpretability and objective. Tocuhed on concepts of
- reliability, scalability, and maintainability
- technical debt
- ML-specific and large scale distributed system failures
- velocity, validation and versioning

---

### 🧰 Tools & Frameworks
Chamelon Cloud intro

---

### 📚 Readings 

- **Case study on Oda, Norwegian grocery delivery service:** [Part 1](https://medium.com/oda-product-tech/how-we-went-from-zero-insight-to-predicting-service-time-with-a-machine-learning-model-part-1-516b9545d02f) and [Part 2](https://medium.com/oda-product-tech/how-we-went-from-zero-insight-to-predicting-service-time-with-a-machine-learning-model-part-2-2-ad8b0c3e4838)
  - Using an ML model to improrve planned service time, which is the non-driving time spent by a driver doing tasks such as picking up orders, scanning codes, parking. Makes up ~50% route times
  - No good data - so they needed to find a proxy or find a way to measure. Went with geofencing, involved drivers from the start to ensure open communication.
  - Geofence service time worked pretty well except for edge cases like multiple houses being in the same radius
  - Features such as order size (weight, number of items, number of boxes), area (for parking), customer data (floor number, previosuly recorded times) were fed into the model.
  - Model details: lightgbm gradient boosting model, Bayesian optimization using optuna library.
  - Tested for six weeks in representative neighborhood. Mean Absolute Error of ML model ~30s better than business-logic based model.
  - Did deploying ML models improve delivery precision and accuracy? A little, but not as much as hoped. Only a reduction of 10% of the delay distribution’s standard deviation (v/s stop density)
  - Why? Reduced precision might not matter as long as the errors even out. Going back to the business-logic based prediciton model, rural stops generally performed better than predicted service time, and urban stops were the opposite. On a route which has a combination of the two, the delay cancelled out. SO business-logic model didn't perform as bad as ML model even though the ML model did have better individual predicitions.
  - But there are other benefits of the ML model: system can be iterated on to better plan routes; feature importance insights, less manual adjustments needed as they expand
  - Future work: filtering out training data, make model deal with drift better (such as due to weather) 

