# Medical Test Management System (Shell Scripting Project)

## Overview

This project implements a **Medical Test Management System** using **Shell Scripting (Bash)**.
It provides a simple and efficient way to **store, manage, retrieve, update, and delete** medical test data for individual patients by interacting with text-based data files.

## Files

*   `MedicalTest.sh`: The main shell script implementing all system functionalities.
*   `MedicalRecord.txt`: The primary data file storing all patient medical test records. Each line represents a single test entry.
*   `MedicalTest.txt`: A reference file containing details about available medical tests, including their normal ranges and units.
*   `Project_Description.pdf`: The original project assignment description and requirements document.

## Data File Formats

*   `MedicalRecord.txt`: Each line follows the format:
    `PatientID: TestName, TestDate, Result, Unit, Status`
    - `PatientID`: 7-digit integer.
    - `TestName`: String (e.g., Hgb, BGT, LDL, systole, diastole).
    - `TestDate`: String in `YYYY-MM` format.
    - `Result`: Floating-point number.
    - `Unit`: String (e.g., mg/dL, g/dL, mm Hg).
    - `Status`: String (`Pending`, `Completed`, or `Reviewed`).

    Example:
    ```
    1300500: Hgb, 2024-05, 14.2, g/dL, Completed
    1300511: LDL, 2024-06, 115.0, mg/dL, Pending
    ```

*   `MedicalTest.txt`: Each line describes an available test and its normal range/unit.
    Example lines based on the project description:
    ```
    Hemoglobin (Hgb); Range: > 13.8, < 17.2; Unit: g/dL
    Blood Glucose Test (BGT); Range: > 70, < 99; Unit: mg/dL
    LDL Cholesterol Low-Density Lipoprotein (LDL); Range: < 100; Unit: mg/dL
    Systolic Blood Pressure (systole); Range: < 120; Unit: mm Hg
    Diastolic Blood Pressure (diastole); Range: < 80; Unit: mm Hg
    ```
    *(Note: The script hardcodes some range checks based on the PDF description, but uses this file for retrieving units during the 'Add' process).*

## Features

The system provides a menu-driven interface with the following functionalities:

1.  **Add a new medical test record:** Prompts for patient ID, test name, date, result, and status with input validation.
2.  **Search for a test by patient ID:**
    *   Retrieve all tests for a given patient ID.
    *   Retrieve upnormal tests for a given patient ID.
    *   Retrieve tests within a specific date range (YYYY-MM) for a given patient ID.
    *   Retrieve tests by status (Pending, Completed, Reviewed) for a given patient ID.
3.  **Search for abnormal tests:** Finds and displays all upnormal test results across *all* patients.
4.  **Calculate average test value:** Computes and displays the average result for each type of medical test recorded in the system.
5.  **Update an existing test:** Allows updating the result, date, or status of a specific test identified by Patient ID, Test Name, and Date. Includes validation.
6.  **Delete a test:** Removes a specific test record identified by Patient ID, Test Name, and Date after confirmation. Includes validation.
7.  **Exit:** Quits the application.

The script includes robust error handling for invalid inputs (e.g., incorrect ID format, invalid date format, wrong status) and provides feedback when patients or tests are not found.

## Requirements

*   Linux Operating System
*   Bash Shell
*   Standard Unix utilities: `grep`, `sed`, `awk`, `cut`, `date`, `bc` (for floating-point arithmetic).
*   `MedicalRecord.txt` (can be empty initially) and `MedicalTest.txt` files located in the same directory as the script.

## How to Run

1.  Save the provided shell script content as `MedicalTest.sh`.
2.  Create (if they don't exist) the `MedicalRecord.txt` and `MedicalTest.txt` files in the same directory. Populate `MedicalTest.txt` with the test definitions as described in the "Data File Formats" section above or the `Project_Description.pdf`.
3.  Open a terminal and navigate to the directory where you saved the files.
4.  Make the script executable:
    ```bash
    chmod +x MedicalTest.sh
    ```
5.  Run the script:
    ```bash
    ./MedicalTest.sh
    ```
6.  Follow the on-screen menu to interact with the system.

