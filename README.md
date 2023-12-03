# Input Validation Assignment Introduction

I have implemented a robust REST API application designed to manage a phone book, maintaining a comprehensive database of names and corresponding phone numbers.

## Instructions for Building and Running Software and Unit Test

To build and run the software, follow these steps:

1. Extract the folder from the zipped version into a new directory.
2. Docker files are created and set up.
3. Build the application using the command: `docker build -t phonebook .`
4. Run the image: `docker run -p 8000:8000 phonebook`
5. Once the build and run process is complete, open a browser window.
6. Navigate to: http://127.0.0.1:8000/list
7. View the list of containers created with the command: `docker ps -a`
8. For testing, use the command: `pytest -s testing.py`. I have attached the screenshot for test cases.
9. Postman screenshots and collection file are attached for further testing.

## Description of How Your Code Works

The implemented REST API application maintains a phone book of names and phone numbers, offering the following API endpoints:

- GET /PhoneBook/list: Lists members of the database.
  ```bash
  curl -X POST "http://localhost:8000/PhoneBook/list"
  ```
- POST /PhoneBook/add: Adds a new person to the database.
  ```bash
  curl -X POST "http://localhost:8000/PhoneBook/add" -H "Content-Type: application/json" -d '{"full_name": "John Doe", "phone_number": "1(703)123-1234"}'
  ```
- PUT /PhoneBook/deleteByName: Removes someone from the database by name.
  ```bash
  curl -X PUT -H "Content-Type: application/json" "http://localhost:8000/PhoneBook/deleteByName?name=John Doe"
  ```
- PUT /PhoneBook/deleteByNumber: Removes someone by telephone number.
  ```bash
  curl -X PUT -H "Content-Type: application/json" "http://localhost:8000/PhoneBook/deleteByNumber?phone_number=1234567890"
  ```

## Audit Logging

Implemented audit logging for debugging purposes, configured server.log file to capture logs.

![image](https://github.com/harsh1102/phoneBook/assets/41270424/c9cd7401-eec5-410b-934b-0310288be0b6)



## Assumptions Made

The following assumptions were considered during the project:

1. Data provided contains valid or invalid inputs for "name" and "number" fields only.
2. Docker is installed for running the application.
3. The URL "http://127.0.0.1:8000/PhoneBook/list?Content-Type=application/json" is opened in the browser.
4. Testing is performed using `pytest -s testing.py`.
5. The provided Postman collection is imported for testing the application. (Secure collection.json)

![image](https://github.com/harsh1102/phoneBook/assets/41270424/85983318-76f5-4291-8582-014f70cc87d9)

## Pros/Cons of Your Approach

**Pros:**
- Data is stored locally using SQLite, providing easy access.
- SQLite's prepared statements reduce the risk of injection attacks as data is verified by the API.

**Cons:**
- Pytest caching may impact test case verification. To address this, stop the server and reload using `uvicorn app:app --reload`.
