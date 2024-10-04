# TrialMatcher

This project aims to match patients to clinical trials based on their medical history and conditions. The matching algorithm checks **inclusion** (age criteria) and **exclusion** criteria (medical conditions and medications) to determine which trials a patient may be eligible for.

Additionally, the system generates:
- **Patient history summaries**.
- **Explanations for why a patient is eligible** for a specific clinical trial.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Data Preprocessing](#data-preprocessing)
- [Patient Matching](#patient-matching)
- [Testing](#testing)
- [Project Structure](#project-structure)
- [License](#license)

## Overview

This system takes patient data (age, medical conditions, and medications) and clinical trial data (age requirements and exclusion criteria), and matches patients to clinical trials for which they are eligible. The matching algorithm performs the following tasks:

1. Verifies if the patient meets the **age criteria** for a trial.
2. Compares the patient’s **medical conditions and medications** against the trial's **exclusion criteria**.
3. Summarizes the patient’s medical history.
4. Generates an explanation for the match, detailing why the patient qualifies for the trial.

The code includes the following two main components:
- **Data Preprocessing** (`data_preprocessing.py`): Cleans, processes, and prepares patient and trial data for matching.
- **Patient Matching** (`patient_matching.py`): Performs the patient-to-trial matching and generates the necessary outputs.

## Features

- **Age-based Inclusion Criteria**: Patients are matched to trials based on age ranges (`minimum_age` and `maximum_age`).
- **Exclusion Criteria Check**: Patients are excluded from trials if their conditions or medications conflict with the trial's exclusion criteria.
- **Patient History Summarization**: Generates a concise summary of the patient’s medical conditions and medications.
- **Match Explanation**: Provides detailed reasoning for why a patient is eligible for a specific trial.
- **Unit and Integration Testing**: The system is fully tested with unit tests and integration tests using sample patient and trial data.

## Installation

To get started with this project, follow these steps:

### Prerequisites

- Python 3.8 or higher
- Libraries:
  - pandas
  - json
  - re
  - unittest (for testing)

### Clone the Repository

```bash
git clone https://github.com/yourusername/clinical-trial-matching.git
cd clinical-trial-matching
```

### Install Dependencies

Ensure that you have all required dependencies installed. You can install the dependencies using `pip`:

```bash
pip install pandas
```

## Usage

### 1. Data Preprocessing

Before running the patient matching system, ensure that your data is preprocessed and cleaned. The `data_preprocessing.py` script handles this step.

#### Running Data Preprocessing:

```bash
python data_preprocessing.py
```

This script performs the following tasks:
- Loads the patient and trial data.
- Cleans and processes data (e.g., formatting age data, handling missing values).
- Saves the processed data to CSV files for use in the matching system.

Ensure that the paths to your input CSV files are set correctly in the `data_preprocessing.py` script.

### 2. Patient Matching

Once the data has been preprocessed, you can run the `patient_matching.py` script to match patients to clinical trials.

#### Running Patient Matching:

```bash
python patient_matching.py
```

You will be prompted to input a **Patient ID**. The system will match the patient to eligible trials and generate an output JSON file with the patient’s history, eligible trials, and explanations.

### 3. Output Example

The output is saved in a file such as `eligible_trials_output_12345.json` and may look like this:

```json
{
  "patientId": "12345",
  "patientSummary": "Patient 12345 Summary:\nMedical Conditions: Hypertension, Diabetes Type 2\nMedications: Lisinopril, Metformin",
  "eligibleTrials": [
    {
      "trialId": "NCT001",
      "trialName": "Hypertension Treatment Study",
      "eligibilityCriteriaMet": [
        "Age requirement met",
        "Exclusion criteria cleared"
      ],
      "explanation": "Patient 12345 with age 45 is eligible for the trial 'Hypertension Treatment Study' (NCT Number: NCT001). The patient's age satisfies the age criteria (40 Years to 65 Years), and the patient's medical conditions and medications do not match any of the exclusion criteria."
    }
  ]
}
```

## Data Preprocessing

The `data_preprocessing.py` script is responsible for:
- Loading patient and trial data.
- Cleaning up missing values, formatting age columns, and preparing the data for matching.
- Saving the preprocessed data to CSV files that can be used by the patient matching system.

Example:

```bash
python data_preprocessing.py
```

Ensure that the paths to the raw patient and trial data files are correctly specified in the script.

## Patient Matching

The `patient_matching.py` script performs the main functionality of the project. It:
- Matches patients to clinical trials based on age and exclusion criteria.
- Summarizes patient history.
- Generates explanations for each eligible trial.
- Saves the output as a JSON file.

Example:

```bash
python patient_matching.py
```

### Command Line Input:
- You will be prompted to enter the **Patient ID**.
- The system will generate a JSON output file that includes the patient summary and eligible trials.

## Testing

The project includes **unit tests** and **integration tests** to ensure the accuracy of the matching system.

### Running Unit Tests

To run the unit tests, execute the following:

```bash
python -m unittest
```

This will run all tests defined in the `TestTrialMatchingFunctions` class and ensure that the individual components work as expected.

### Running Integration Tests

You can run an integration test by using sample patient and trial data to ensure that all components work together correctly. Sample data is included in the `patient_matching.py` file for testing.

## Project Structure

```
├── README.md               # Project documentation
├── data_preprocessing.py    # Data preprocessing script
├── patient_matching.py      # Main Python script for matching patients to trials
├── eligible_trials_output.json  # Output file for matched trials
├── tests/                   # Contains unit tests
└── sample_data/             # Sample patient and trial data (for testing)
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
