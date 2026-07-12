

# Track: C – Model Prediction Explanation Pipeline

# Project Objective

The objective of this project is to load a trained Machine Learning model, generate predictions for three feature-vector inputs, and use a Large Language Model (LLM) to explain those predictions in simple language. The LLM returns the explanation in JSON format, which is validated using a JSON Schema. A PII Guardrail is also implemented to prevent sensitive information from being sent to the LLM.

# Project Structure

TrackC_Project/
TrackC.ipynb
best_model.pk1
cleaned_data.csv
.env

# Load Dataset

**Dataset used** 
cleaned_data.csv
**Dataset is loaded using**
import pandas as pd
df = pd.read_csv("cleaned_data.csv")

# Load Trained Model

Model file:
best_model.pk1

Load the model:
model = joblib.load("best_model.pk1")

# Create Three Feature Vectors
Three records are selected from the dataset.

The feature columns include:
- actual_price
- discount_percentage
- rating
- rating_count
- category

# Make Predictions

The model predicts:

- Prediction Label
- Prediction Probability

# Create System Prompt
# Create User Prompt

The user prompt contains:

- Feature values
- Prediction
- Prediction probability

Actual Price: 1099.0
Discount Percentage: 64.0
Rating: 4.2
Rating Count: 24269.0
Category: Computers&Accessories|Accessories&Peripherals|Cables&Accessories|Cables|USBCables
Predicted Class: 0
Prediction Probability: 0.98

# Call the LLM

The OpenRouter API is used to generate explanations.

Model:
openai/gpt-4.1-mini

Temperature:0

**Reason**: Temperature 0 produces deterministic and consistent responses, making it ideal for structured JSON output.

# JSON Schema

# Validate JSON

The LLM response is validated using **jsonschema**.

# Valid output:
JSON Validation passed

# Invalid output:
JSON validation Failed

# PII Guardrail

The project checks the prompt for Personally Identifiable Information (PII).
The guardrail detects:

- Email addresses
- Phone numbers
Input blocked: PII detected.

# Purpose:
- Protect user privacy
- Prevent sensitive information from reaching the LLM
- Improve application security

# Temperature Comparison

| Temperature | Result |
|-------------|--------|
| 0 | Stable, deterministic JSON output |
| 0.7 | More creative but responses vary |

Temperature **0** was selected for this project because it provides consistent and reliable outputs.

# Prediction Examples

The pipeline was tested using three feature vectors from **cleaned_data.csv**.

For each input:

- Features were extracted.
- Prediction was generated.
- Prediction probability was calculated.
- LLM explanation was produced.
- JSON output was validated.

---

# API Configuration

The API key is stored securely in the `.env` file.

os.environ["OPENROUTER_API_KEY"] = userdata.get("OPENROUTER_API_KEY")

The API key is not hardcoded into the notebook.

# Output

For each test record, the notebook displays:

- Input features
- Predicted label
- Prediction probability
- JSON explanation
- Validation result

# Conclusion

This project successfully demonstrates a complete Machine Learning explanation pipeline. A trained Random Forest model predicts outcomes from product features, while an LLM provides clear, structured explanations. JSON Schema validation ensures the output format is correct, and a PII Guardrail protects user privacy by preventing sensitive information from being processed. The use of **temperature = 0** ensures consistent and reliable explanations suitable for real-world deployment.
