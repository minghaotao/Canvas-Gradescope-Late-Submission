# Educause Poster Presentation 2023


Gradescope is integrated within Canvas but won't pass the submission time to Canvas. For instructors who would like to use Canvas Late Policy for Gradescope submissions, this project has demoed an automated way to script the late submission time from the Gradescope course, then upload the late submission time to the Canvas on behalf of the student. 


# Code Documentation

This repository contains a collection of Python scripts designed to interact with the Gradescope and Canvas platforms for managing student data, late submissions, and assignment grades. Below is an overview of each script and its functionality.

## `file_mapping.py`

This script contains mappings and configurations related to courses, assignments, and filters. Here's a breakdown of its contents:

- `course_url`: A dictionary that maps course numbers to their Gradescope URLs.
- `canvas_id_map`: A mapping of course numbers to Canvas Course IDs.
- `assignment_map`: Maps course numbers to assignments, linking assignment names to Canvas Assignment IDs.
- `filters`: Specifies which columns should be included in the data for each course number.

## `Gradescope.py`

`Gradescope.py` defines functions to interact with the Gradescope platform for downloading, processing, and analyzing student data. Key functions include:

- `download_data(course_number)`: Downloads student data from the specified course using the Gradescope API and returns it as a Pandas DataFrame.
- `clear_file()`: Clears the contents of a CSV file to prepare for new data.
- `late_columns(df)`: Extracts columns related to lateness from the DataFrame.
- `get_canvas_course_id(df)`: Extracts Canvas Course IDs from the DataFrame.
- `get_late_submission_time(df, late_column_name, course_number)`: Processes late submission data and saves it to a CSV file.
- `read_data(course_number)`: Coordinates the data extraction and transformation process for a given course.
- `run_files()`: Initiates the data processing for all configured courses.

## `main.py`

`main.py` serves as the entry point for running the entire workflow, including interactions with the Canvas API and Slack notifications. Key functions and tasks include:

- `load_json()`: Loads Slack credentials from a JSON file.
- `slack_bot(message=None, type=None)`: Sends messages and files to Slack channels.
- Functions for interacting with the Canvas API:
  - `get_student_id(student_id)`: Retrieves Canvas User IDs based on SIS User IDs.
  - `check_student_enrollment(student_id, course_id)`: Checks if a student is enrolled in a specific course.
  - `check_submission_time(course_id, assignment_id, user_id)`: Retrieves submission times for assignments.
  - `upload_submission_time(course_id, assignment_id, user_id, submission_time)`: Uploads submission times to Canvas.
- `access_files()`: Processes late submissions, checks submission times, and uploads them to Canvas.
- The `if __name__ == '__main__':` block initiates the workflow when the script is run.

## `SEAS_Canvas.py`

`SEAS_Canvas.py` defines a class, `Canvas`, for interacting with the Canvas API. It includes methods for managing assignments, grades, and user data.

Please note that certain aspects of the code, such as file paths and credentials, are configured for specific environments and may require customization to work in different setups.

Before running the code, ensure that you have the necessary API credentials, file paths, and dependencies installed.

This README.md provides an overview of the code's functionality, but further details on how to set up and configure the code may be needed depending on your specific use case and environment.





# Credits: 

Thank you, Ben Rosen, Courseware Developer at UPenn for helping me solve the error message when posting the student's submission time to Canvas-Gradescope assignment. 


Thank you, Ira Winston at Penn Engineering online for helping me figure out how to use Browser Cookies to authenticate Gradescope.  



