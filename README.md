# 📊 Instagram Performance & Engagement Analytics

*A full-cycle social media analytics project built from scratch using Python & Power BI*

---

##  Project Overview

This project is an **end-to-end social media analytics dashboard** built using simulated Instagram data, with the goal of understanding **content performance, engagement quality, growth drivers, and optimal posting strategy**.

What makes this project different is not just the final dashboard, but the **entire analytical journey** ; from raw dataset design, feature engineering, metric validation, debugging aggregation pitfalls, to professional dashboard storytelling.

This project was intentionally treated like a **real-world analytics problem**, where data is imperfect, assumptions must be questioned, and insights must be defensible.

---

##  Business Questions Addressed

The dashboard answers the following key questions:

* How is overall engagement and reach trending?
* Which content formats and categories drive **high-quality engagement** (saves & shares)?
* What discovery sources contribute most to follower growth?
* How does engagement change as audience size increases?
* What is the **best time and day** to post for higher engagement?
* Do weekends perform better than weekdays?

---

##  Dataset Description

The dataset is **synthetic and educational**, created to simulate real Instagram post-level analytics.

### Initial Columns Included:

* `post_id`
* `upload_date`
* `media_type`
* `likes`, `comments`, `shares`, `saves`
* `reach`, `impressions`
* `caption_length`
* `hashtags_count`
* `traffic_source`
* `content_category`
* `followers_gained`

### Additional Columns Engineered During the Project:

* `account_id` (creator-level grouping)
* `followers_count_before_post` (baseline audience size)
* `engagement_rate` (validated and corrected via DAX)
* `post_hour`, `post_day`, `is_weekend`
* `has_high_hashtags`, `long_caption`
* `high_intent_engagement` (saves + shares)
* `follower_bucket` (Small / Medium / Large / Very Large)

dataset link- https://www.kaggle.com/datasets/kundanbedmutha/instagram-analytics-dataset
>  Several columns were **reworked after discovering logical or analytical issues**, reflecting real-world data refinement.

---

##  Tools & Technologies Used

* **Python**

  * Pandas, NumPy
  * Data cleaning, feature engineering, data validation
* **Power BI**

  * Power Query (data shaping & enrichment)
  * DAX (measures & time intelligence)
  * Data modeling (Date dimension, relationships)
  * Interactive dashboards

---

##  Key Challenges Faced & How They Were Solved

### 1️ Engagement Rate Aggregation Bug

**Problem:**
Engagement rate was initially aggregated using `SUM`, producing meaningless values (>100%).

**Solution:**

* Identified engagement rate as a **ratio metric**
* Rebuilt it using a **DAX measure**:

  ```
  Engagement Rate = Total Engagement / Total Reach
  ```
* Ensured all visuals used measures, not columns

 *This step alone significantly improved analytical correctness.*

---

### 2️ Creator & Follower Baseline Modeling

**Problem:**
Raw data had no concept of creators or follower baselines.

**Solution:**

* Introduced `account_id`
* Assigned creators across multiple posts (non-uniform distribution)
* Generated `followers_count_before_post` to analyze growth impact

This enabled **creator-level and scale-based insights**.

---

### 3️ Date & Time Intelligence Issues

**Problem:**

* Slicers partially worked
* Start date didn’t affect KPIs
* Sorting by weekday failed

**Solution:**

* Built a dedicated **Date dimension table**
* Linked it properly to the fact table
* Used `Weekday Number` for logical sorting
* Marked Date table correctly for time intelligence

---

### 4️ Posting Time Analysis Blocked by Data

**Problem:**
All posts had the same posting hour (`post_hour = 9`), making timing analysis impossible.

**Root Cause:**
Synthetic timestamps lacked realistic variation.

**Solution:**

* Regenerated `post_hour` realistically in **Power Query**
* Ensured values were stable (non-random on refresh)
* Revalidated visuals after refresh

This unlocked **Page 3 (Posting Strategy & Timing)**.

---

### 5️ Sorting & Visual Integrity Problems

**Problem:**
Text-based categories (weekday, follower bucket) would not sort correctly.

**Solution:**

* Ensured sort keys existed in the **same table**
* Used “Sort by Column” correctly
* Avoided cross-table sorting mistakes

---

##  Dashboard Structure

###  Page 1 — Executive Overview

Focus: **High-level performance snapshot**

* Total Engagement
* Engagement Rate (%)
* Followers Gained
* Average Reach per Post
* Total Posts
* Engagement by Media Type
* Post Distribution
* Discovery Sources vs Growth

---

###  Page 2 — Content Performance & Growth Drivers

Focus: **Why certain content performs better**

* Engagement Rate by Media Type
* High-Intent Engagement by Content Category
* Hashtag Usage vs Engagement
* Caption Length vs Engagement
* Follower Growth by Traffic Source
* Engagement vs Audience Size (Follower Buckets)

---

###  Page 3 — Posting Strategy & Timing

Focus: **Actionable posting recommendations**

* Best Time of Day to Post
* Engagement by Day of Week
* Weekend vs Weekday Performance
* Best Posting Hours: Weekday vs Weekend

---

##  Key Analytical Learnings

* **Ratios should never be summed** — always use measures
* Default Power BI aggregations can mislead if not questioned
* Synthetic data still requires **realistic assumptions**
* Good dashboards are built through **iteration, debugging, and validation**
* White space is intentional; not every page needs to be “filled”

---

##  Why This Project Matters

This project reflects:

* Analytical thinking, not just visualization
* Real-world debugging skills
* Understanding of metric correctness
* Ability to turn messy data into structured insights
* End-to-end ownership of an analytics problem

It is designed to be **portfolio-ready, interview-defensible, and extensible**.

---

##  Future Enhancements

* Add YoY / MoM engagement trends
* Simulate paid vs organic content
* Introduce sentiment analysis on captions
* Build creator-level drill-through pages

---

##  Final Note

This project was not about “making charts”.
It was about **thinking like an analyst**, questioning assumptions, fixing mistakes, and telling a data-backed story.

Always open towards Feedbacks and Discussions 😊
---

