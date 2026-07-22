# Interactive Parent-Child Activity Planner

## Overview

The Interactive Parent-Child Activity Planner is a web-based application that recommends activities for parents and children to enjoy together. By analyzing shared hobbies and interests, the platform provides tailored suggestions to enhance family bonding and create memorable experiences.

## Aim

The key objectives of this project are as follows:

- **User Input Collection:** Gather details about the child’s interests, age, and preferences.
- **ML Model Integration:** Utilize a trained machine learning model to predict suitable hobbies.
- **Activity Retrieval from Database:** Fetch activities from MongoDB based on predicted hobby and age group.
- **Personalized Recommendations:** Generate customized activity suggestions.
- **Interactive UI:** Provide an intuitive and user-friendly interface for parents.

## Demo

Experience the live application: [Interactive Parent-Child Activity Planner](https://interactive-parent-child-activity-planner.onrender.com/)

## Dataset Description

The dataset used for training the model contains various child interests, age groups, and activity preferences. The structured data allows the model to identify patterns and suggest the most relevant activities.

- **Dataset Source:** [Hobby Prediction Dataset](https://www.kaggle.com/datasets/abtabm/hobby-prediction-basic/data)
- **Features:**
  - Child’s age (categorized into **4-5** and **6-8** years)
  - Interests (Arts, Sports, Academics)
  - Preferred activity type (indoor, outdoor)
  - Time availability
  - Parental participation level

## How It Works

1. **User Input Handling:** Collects child-related details through a form.
2. **ML Model Prediction:** The trained model predicts the child's hobby (Arts, Sports, or Academics).
3. **Fetching Data from MongoDB:** Based on the predicted hobby and age group, the system retrieves activity recommendations from the MongoDB database.
4. **Recommendation Display:** Presents the personalized recommendations (videos, descriptions, required materials) on the web interface.

## MongoDB Database Structure

The database stores activities under three categories: **Arts, Sports, and Academics**, further classified into two age groups (**4-5** and **6-8**). Each activity entry includes:

- **URL**: A link to an instructional video.
- **Title**: Activity name.
- **Description**: Brief details about the activity.
- **Image**: Stored as a Base64 binary.
- **Materials**: List of required materials.
- **Duration**: Estimated time to complete the activity.
- **Age Group**: Either **4-5** or **6-8**.

## Model Training and Evaluation

The machine learning models used in this project were trained using a dataset from Kaggle.

- Dataset: Hobby Prediction Dataset
- Libraries Used: pandas, numpy, matplotlib, seaborn, sklearn

## Models Implemented:

1. RandomForestClassifier (Primary Model)
2. Logistic Regression

## Model Evaluation:

- Metrics Used:

  - Accuracy Score
  - Classification Report
  - Confusion Matrix

- Performance on Test Data:
  - Achieved 91% accuracy

## Hyperparameter Tuning:

- Used GridSearchCV to optimize the model parameters.
- Improved model performance by tuning hyperparameters for better accuracy.

## Usage

To set up and run the project:

1. Clone the repository:

```bash
git clone https://github.com/DiyaBhujbal/Parent-child-Activity-Planner.git
cd Parent-child-Activity-Planner
```

2. Create and Activate a Virtual Environment:

```bash
python3 -m venv venv
source venv/bin/activate  # On Windows, use venv\Scripts\activate
```

3. Install Dependencies:

```bash
pip install -r requirements.txt
```

4. Run the Application:

```bash
python app.py
```

Access the application at http://127.0.0.1:5000/ in your browser.

## Conclusion

This project aims to enhance parent-child engagement by leveraging machine learning to recommend personalized activities. The combination of a user-friendly web interface, an optimized ML model, and a structured MongoDB database ensures a seamless experience for parents looking to spend quality time with their children.
