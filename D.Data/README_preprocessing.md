# 📄 README_preprocessing — Data Preparation

## Common Preprocessing Steps

The following common preprocessing steps are performed in all notebooks:

- **Target Variable Formation:** `target = like + dislike` in the training dataset.
- **Memory Optimization:**
  - Data type conversion (`category`, `int`, `float`) to minimize data size.
- **Saving New Datasets:**
  - After preprocessing, the data is saved for quick model training.

These steps are applied in each notebook to reduce data size and simplify the structure.

---

## 📄 fv2 — Initial Preprocessing

### What has been done:
- **Additional Features:**
  - Added features: `age`, `item_duration` via the `CONFIG` configuration.

---

## 📄 fv3 — Secondary Preprocessing

### What has been done:
- **Additional Features:**
  - Added features: `age`, `gender`, `duration`, `source_id`.
  - Integrated video content embeddings (`embeddings`) into the training and test datasets.

---

## 📄 av1 — Extended Preprocessing

### What has been done:
- **Additional Features:**
  - Added features at the user, item, and source levels:
    - **User-level features:** `age`, `gender`, `user_like_ratio`, `user_dislike_ratio`, `user_ignore_ratio`, `user_share_ratio`, `user_bookmark_ratio`, `user_avg_spent_time`, `user_view_ratio`, `user_full_view_ratio`.
    - **Item-level features:** `item_duration`, `item_like_ratio`, `item_dislike_ratio`, `item_ignore_ratio`, `item_share_ratio`, `item_bookmark_ratio`, `item_avg_spent_time_ratio`, `item_view_ratio`, `item_full_view_ratio`.
    - **Source-level features:** `source_id`, `source_like_ratio`, `source_dislike_ratio`, `source_ignore_ratio`, `source_share_ratio`, `source_bookmark_ratio`, `source_avg_spent_time_ratio`, `source_view_ratio`, `source_full_view_ratio`.

