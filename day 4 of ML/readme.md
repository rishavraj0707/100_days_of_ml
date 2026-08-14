# Machine Learning Types: Batch vs Online Learning

##  Batch Learning

Batch learning trains a model on the **entire dataset at once** and keeps it unchanged until the next retraining cycle.

### Process

1. Train on the full dataset.
2. Test and validate.
3. Deploy the model.
4. Retrain periodically.

### Use Cases

* Recommendation systems
* Spam classifiers
* Sentiment analysis

---

##  Online Learning

Online learning updates the model **incrementally as new data arrives**.

### Process

1. Receive new data.
2. Update the model incrementally.
3. Adapt to changing patterns.
4. Continue learning over time.

### Benefits

* Adapts quickly to new trends.
* Handles **concept drift**.
* Works well with streaming data.
* Doesn't require full retraining for every update.

---

##  Key Differences

| Aspect       | Batch Learning      | Online Learning       |
| ------------ | ------------------- | --------------------- |
| Training     | Full dataset        | Incremental data      |
| Updates      | Periodic            | Continuous            |
| Adaptability | Lower               | Higher                |
| Data         | Mostly static       | Continuously changing |
| Best for     | Stable environments | Dynamic environments  |

---

##  When to Use Which?

**Choose Batch Learning when:**

* Data changes slowly.
* You need thorough testing before deployment.
* Periodic retraining is sufficient.

**Choose Online Learning when:**

* Data changes continuously.
* Real-time adaptation is important.
* You have streaming data.
* Concept drift is common.

---

##  Examples

**Batch Learning:**
A movie recommendation system is trained on user and movie data and updated weekly.

**Online Learning:**
A social media recommendation system continuously learns from user interactions and trending content.

---

##  Important Considerations

* **Concept Drift:** Online learning adapts better to changing patterns.
* **Computational Cost:** Batch learning can require more resources during retraining.
* **Model Freshness:** Online learning keeps models more up to date.
* **Connectivity:** Online learning often depends on continuously available data.

##  Conclusion

**Batch Learning** is best for stable data and periodic updates, while **Online Learning** is better for dynamic environments that require continuous adaptation.

---