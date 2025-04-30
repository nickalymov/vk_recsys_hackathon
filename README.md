# 🎯 VK RecSys Challenge – AI VK Explicit Feedback Prediction

🧠 Participated in the competition for predicting user likes and dislikes on VK Clips from AI VK.

📊 **Result**: 13th place out of 465 teams  
💡 **ROC-AUC**: `0.6666753935` on the private leaderboard

## 📝 Task

Build a model predicting explicit feedback (like / dislike / ignore) from users towards videos in VK Clips.

### 🎯 Target Metric
Multiclass ROC-AUC for three labels:  
- `like = 1`  
- `dislike = -1`  
- `ignore = 0`

## 📂 Data

**Training dataset** – User interactions with clips over 6 weeks:  
- `user_id`, `item_id`, `timespent`, `like`, `dislike`, `share`, `bookmarks`

**User metadata**:
- `user_id`, `gender`, `age`

**Clip metadata**:
- `item_id`, `source_id`, `duration`, `embeddings` (neural embeddings of multimodal content)

**Test dataset**:
- Pairs `(user_id, item_id)` from week 7 requiring predictions.

## 🧠 Best Solution

🔗 [Notebook](https://github.com/nickalymov/vk_recsys_hackathon/blob/main/8.1_test.ipynb)  
🔗 [Submission File](https://github.com/nickalymov/vk_recsys_hackathon/blob/main/8.1_test_e0.csv.7z)

The model uses DCNv2 with historical interaction embeddings and object metadata. A hybrid architecture combining Deep & Cross networks integrates item/user features and dynamically updated user interaction histories (like / dislike / ignore).

---

## 🔧 Model Architecture

- **Input Features**:
  - Categorical embeddings: `user_id`, `item_id`, `source_id`, `gender`, `age`, `duration_sec`.
  - `item_embed`: static item embedding (32).
  - `user_history_embed`: interaction embedding (96 = 3 × 32), built from 3 interaction histories:
    - like / dislike / ignore — average of cosine-similar objects.

- **Model**:
  - DCNv2:
    - 3 CrossNet layers.
    - 3 MLP layers.
  - Dropout + LayerNorm.
  - Classification on 3 classes: `0` = dislike, `1` = ignore, `2` = like.

---

## ⚙️ Training

- Loss: `CrossEntropyLoss`.
- Optimizer: `Adam`, `lr=0.001`.
- Periodic update of interaction histories.
- Model output — class probabilities converted to scores.

## 🧪 Inference

- For each user in `test_pairs.csv`, calculate interaction embeddings using data from `train_interactions`.
- Predictions are made following the same principles as in training.

---

## ❌ Areas for Improvement

- 🎥 **Full interaction history processing with sequential models**  
  Instead of simply aggregating (mean pooling) embeddings of liked / disliked / ignored items, more expressive architectures such as **Transformer**, GRU, or attention pools could be used to model **temporal dependencies** and interaction context.  
  Top participants used this approach, feeding the **entire sequence of interactions** into the model, which improved performance by accounting for the order and depth of the history.

🔗 [Top Solutions](https://ods.ai/competitions/aivkchallenge/video)

---

## 📎 Competition Link

🔗 [Data and competition description on ODS.ai](https://ods.ai/competitions/aivkchallenge/dataset)
