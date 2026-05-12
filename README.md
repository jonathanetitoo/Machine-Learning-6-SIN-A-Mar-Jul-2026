# ML Final Project — Linear & Logistic Regression
## Student Performance (UCI) · Branch p2

**Pair members:**
- Donato Oña
- Guillermo Paredes

---

## Dataset

**Student Performance Data Set** (UCI Machine Learning Repository, ID 320).  
The dataset is loaded directly using `fetch_ucirepo`, which provides both the input features and target variables already separated.

It contains information about secondary school students in Portugal, including demographic, social, and academic-related attributes.

### Features and Targets

- **Features (X):** student personal, family, and academic background variables  
- **Targets (y):**
  - G1 (first period grade)  
  - G2 (second period grade)  
  - G3 (final grade)

For this project, features and targets are combined into a single DataFrame for easier analysis:

```python
df = pd.concat([X, y], axis=1)

---

## Tool Choice & Justification

We chose **Pandas** for wrangling and **TensorFlow/Keras** for modeling.
Pandas because the dataset fits comfortably in memory (~1k rows) and the
vectorized DataFrame API is the most expressive for EDA and categorical
feature engineering — Polars would be overkill here. TensorFlow because
the Keras Sequential API lets us implement linear and logistic
regression as limit cases of a 1-layer network, while keeping explicit
control over L2 regularization via `kernel_regularizer` and over the
learning rate of the Adam optimizer — two core concepts from the
syllabus. This demonstrates the mathematical equivalence between
classical regression and a single-layer perceptron, strengthening the
conceptual understanding of gradient descent.

---

## How to run (3 commands)

```bash
git clone https://github.com/donatoubs/Machine-Learning-6-SIN-A-Mar-Jul-2026.git
cd Machine-Learning-6-SIN-A-Mar-Jul-2026 && git checkout p2

---

## Results

| Model               | Metric     | Test value |
|---------------------|------------|------------|
| Linear Regression   | R²         | 0.8496     |
| Linear Regression   | MAE        | 0.7632     |
| Linear Regression   | RMSE       | 1.2110     |
| Logistic Regression | Accuracy   | 0.6154     |
| Logistic Regression | Precision  | 0.8750     |
| Logistic Regression | Recall     | 0.6364     |
| Logistic Regression | F1         | 0.7368     |
| Logistic Regression | ROC-AUC    | 0.5323     |

---

## AI usage

- **Claude (Anthropic):** assistance to structure the notebook according
  to the rubric, draft the interpretation paragraphs and review the
  Docker + UV pattern. All code was executed, understood and verified
  by both pair members.

