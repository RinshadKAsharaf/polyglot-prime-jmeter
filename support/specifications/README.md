
# CSV Validation via Frictionless

## Overview

This project leverages the [Frictionless Data](https://frictionlessdata.io/) library to validate CSV files against predefined schemas, ensuring data quality and consistency. The validation process checks data integrity, format adherence, and schema compliance to streamline data workflows.

## Folder Structure

- **`support/specifications`**
  - `datapackage-nyher-fhir-ig-equivalent.json`: Schema specification for validating CSV files.
  - `validate-nyher-fhir-ig-equivalent.py`: Python script to validate CSV files against the schema.
- **`flat-file/nyher-fhir-ig-example/`**: Folder containing sample CSV files for validation.
  - `DEMOGRAPHIC_DATA_partner1-test-20241128-testcase1.csv`: Demographic information data.
  - `QE_ADMIN_DATA_partner1-test-20241128-testcase1.csv`: QE administration data.
  - `SCREENING_OBSERVATION_DATA_partner1-test-20241128-testcase1.csv`: Primary screening observation data.
  - `SCREENING_LOCATION_DATA_partner1-test-20241128-testcase1.csv`: Location-related screening data.
  - `SCREENING_ENCOUNTER_DATA_partner1-test-20241128-testcase1.csv`: Encounter-related screening data.
  - `SCREENING_CONSENT_DATA_partner1-test-20241128-testcase1.csv`: Consent-related screening data.
  - `SCREENING_RESOURCES_DATA_partner1-test-20241128-testcase1.csv`: Detailed screening resources data.
  - `Consolidated NYHER FHIR IG Examples.xlsx`: Excel file with consolidated sheets of the CSV data above.

- **`documentation.auto.md`**
  - Auto-generated documentation detailing the schema, validation process, and CSV contents for easier understanding.

## Prerequisites


Before you can use this tool, make sure you have the following installed on your system:

- **Python 3.x**:
  Ensure that Python 3 is installed on your system. You can check if Python 3 is already installed by running the following command:

  ```bash
  python3 --version
  ```
  If Python 3 is not installed, follow the instructions below to install it:
    - Ubuntu/Debian-based systems:
      ```bash
      sudo apt update
      sudo apt install python3
      ```
    - macOS (using Homebrew):
      ```bash
      brew install python
    - Windows: Download and install the latest version of Python from the official website: https://www.python.org/downloads/

- **pip (Python Package Installer)**: pip is the package manager for Python and is needed to install libraries like Frictionless.

  Check if pip is installed by running:
  ```bash
  python3 -m pip --version
  ```
  If pip is not installed, follow these steps:
    - On Ubuntu/Debian-based systems:
      ```bash
        sudo apt install python3-pip
      ```
    - On macOS (using Homebrew):
      ```bash
        brew install pip
      ```
    - On Windows: If pip isn't already installed with Python, you can get it from the [official Python pip installation guide](https://pip.pypa.io/en/stable/installation/).

  ***Troubleshooting***: 
    If you encounter errors like No module named ensurepip, it's possible that your Python installation is missing the ensurepip module, which is typically used to install pip. In this case, install pip manually using the package manager for your operating system, as described above. Alternatively, you can use the following command to install pip if it's missing:
      ```bash
        python3 -m ensurepip --upgrade
      ```


- **Frictionless**: Once Python 3 and pip are set up, you can install the Frictionless library by running the following command:
  ```bash
  pip install frictionless
  ```
  Visit the [Frictionless Documentation](https://framework.frictionlessdata.io/docs/getting-started.html) for more information.

## Validation Process

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/tech-by-design/polyglot-prime.git
   cd polyglot-prime/support/specifications
   ```

2. **Run the Validation Script**:
   Use the provided `validate-nyher-fhir-ig-equivalent.py` script to validate all CSV files in the `flat-file/nyher-fhir-ig-example/` directory. Replace filenames as necessary, but **ensure that the file order remains unchanged**. The order of files is mandatory for the validation process.

   ```bash
   python validate-nyher-fhir-ig-equivalent.py datapackage-nyher-fhir-ig-equivalent.json flat-file/nyher-fhir-ig-example/QE_ADMIN_DATA_partner1-test-20241128-testcase1.csv flat-file/nyher-fhir-ig-example/SCREENING_OBSERVATION_DATA_partner1-test-20241128-testcase1.csv flat-file/nyher-fhir-ig-example/SCREENING_LOCATION_DATA_partner1-test-20241128-testcase1.csv flat-file/nyher-fhir-ig-example/SCREENING_ENCOUNTER_DATA_partner1-test-20241128-testcase1.csv flat-file/nyher-fhir-ig-example/SCREENING_CONSENT_DATA_partner1-test-20241128-testcase1.csv flat-file/nyher-fhir-ig-example/SCREENING_RESOURCES_DATA_partner1-test-20241128-testcase1.csv flat-file/nyher-fhir-ig-example/DEMOGRAPHIC_DATA_partner1-test-20241128-testcase1.csv output.json
   ```

3. **Review Validation Results**:
   Validation results will be saved in `output.json`, detailing any schema mismatches, errors, or warnings.

4. **Understanding `documentation.auto.md`**:
   - The `documentation.auto.md` file is auto-generated and provides a breakdown of the schema's structure, constraints, and expected field details.
   - Use this file as a reference to interpret validation results and align your CSV data with the schema requirements.

## Notes

- The `datapackage-nyher-fhir-ig-equivalent.json` defines schema expectations, including data types, constraints, and relationships.
- The `validate-nyher-fhir-ig-equivalent.py` script integrates with Frictionless for accurate and detailed validation.
- The `output.json` file provides a machine-readable validation report. To understand its structure, refer to the [Frictionless JSON documentation][(https://framework.frictionlessdata.io/docs/guides/validate](https://framework.frictionlessdata.io/docs/guides/validating-data.html)).

## About the File Naming Convention

The CSV file names in this project follow a strict naming convention to ensure consistency and compatibility with the validation process. Each file name is structured as follows:

**`<DATA_TYPE>_<GROUP_IDENTIFIER>.csv`**

### Components of the File Name

1. **`<DATA_TYPE>`**:
   - This is the predefined and mandatory part of the file name. It indicates the type of data contained in the file and must remain unchanged.
   - Examples of valid values:
     - `DEMOGRAPHIC_DATA_`
     - `QE_ADMIN_DATA_`
     - `SCREENING_CONSENT_DATA_`
     - `SCREENING_OBSERVATION_DATA_`
     - `SCREENING_LOCATION_DATA_`
     - `SCREENING_ENCOUNTER_DATA_`
     - `SCREENING_RESOURCES_DATA_`

2. **`<GROUP_IDENTIFIER>`**:
   - This part of the file name is flexible and includes the following components:
     - **QE Name or Organization**: Represents the entity providing the data (e.g., `partner1-test`).
     - **Date**: The date the data was generated or collected, formatted as `YYYYMMDD` (e.g., `20241128`).
     - **Test Case or Scenario Identifier**: A specific identifier to distinguish different test cases or scenarios (e.g., `testcase1`).

### Example File Names

- `DEMOGRAPHIC_DATA_partner1-test-20241128-testcase1.csv`
- `QE_ADMIN_DATA_partner1-test-20241128-testcase1.csv`
- `SCREENING_CONSENT_DATA_partner1-test-20241128-testcase1.csv`
- `SCREENING_OBSERVATION_DATA_partner1-test-20241128-testcase1.csv`
- `SCREENING_LOCATION_DATA_partner1-test-20241128-testcase1.csv`
- `SCREENING_ENCOUNTER_DATA_partner1-test-20241128-testcase1.csv`
- `SCREENING_RESOURCES_DATA_partner1-test-20241128-testcase1.csv`

### Notes

- **Mandatory Prefix**: The `<DATA_TYPE>` section of the file name is predefined and must not be altered.
- **Customizable Group Identifier**: The `<GROUP_IDENTIFIER>` section can be customized as per the data submission or testing requirements but must adhere to the format `QE-Name-Date-TestCase`.

This naming convention helps ensure files are easily identifiable and properly linked to their corresponding data specifications in validation and analysis.

## Field Descriptions

Field descriptions for each field are documented in the `documentation.auto.md` file. These descriptions include detailed information such as:

- **Description**: The exact path in the FHIR resource from where the field is derived.
- **Example Fields**:
  - **`PATIENT_MR_ID_VALUE`**:
    - **Description**: `Bundle.entry.resource.where(resourceType = 'Patient').identifier.where(type.coding.code = 'MR').value` 
  - **`FACILITY_ACTIVE`**:
    - **Description**: `Bundle.entry.resource.where(resourceType = 'Organization').active` 

Refer to `documentation.auto.md` for the complete set of field descriptions, including FHIR File Paths.


This naming convention helps organize files systematically and allows easy identification of the data source, purpose, and context.

For further assistance, raise a query in the project's [GitHub Issues](https://github.com/tech-by-design/polyglot-prime/issues).
