# Data Integration Challenge
This is the Data Integration Challenge project<br />

## Purpose: 
  this document contains necessary information to run the application and explain the purposes and expected results.<br />
<br />
Customer: NW <br />
Developer: Arthur Flores Duarte <br />
<br />
Created Date: 2018/10/22 <br />
Last Updates:  <br />
<br /><br />

## How to run the application:
  1. First of all, files "appfull.py" and "q1_catalog.csv" should be in the same directory.<br />
  
  2. Execute the python script "appfull.py" to load companies file and start the API ("python appfull.py"); <br />
  
  3. Use the URL http://*[app_host]*:*[app_port]*/company to call the API, and use GET or PUT methods sending JSON contents. Example http://127.0.0.1:5000/company - GET - JSON Content: {"company_name": "pizza hut" , "zip_code": "44667"} <br />
  
  4. If you want, you can test the API by running the test client script "client_test.py" to update and get companies using the API ("python client_test.py"). Files "q2_clientData.csv" and "client_test.py" should be in the same directory;
<br /><br />

## Project Files:
  ###  appfull.py - Main application: load data and starts API
- Setup: 
  - Loads companies data from the initial file (q1_catalog.csv) or persisted file (companies_v001.pkl) to a dataframe;
  - Prepares and transform data;<br />
  - Creates an instance from entity Companies;

- API:
  - Setup API using FLASK framework package;
  - Class Company (Resource);
    - Methods:
      - get : HTTP GET method - search a company by name and zip code.
        - Input: <br />
              HTTP Request - GET - http://127.0.0.1:5000/company<br />
              Name and ZipCode should be informed in JSON content, example:<br />
                {"company_name": "pizza hut" , "zip_code": "44667"}<br />
              <br />
        - Results: <br />
              200: in case of the company was found, return HTTP code "200" and also the company information;<br />
              404: if didn't find any company related, return HTTP code "404 and the message "company not found"; <br /><br />
      - put: PUT HTTP method - update a company website information.
        - Input: <br />
            HTTP Request - PUT - http://127.0.0.1:5000/company <br />
            Name, ZipCode and Website should be informed in JSON content, example: <br />
            {"company_name": "tim dieball", "zip_code": "53115", "website": "http://motorsport-coatings.com" } <br /><br />
        - Results: <br />
            200: in case of the company was found, update the company website attribute and persist companies data in a pickle file (companies_v001.pkl). Then return HTTP code "200" and also retrieve the updated company information;<br />
            404: if didn't find any company related, return HTTP code "404 and the message "company not found"; <br /><br />
  - Finally the code run the API interface to be available:<br />
          URL: http://127.0.0.1:5000/company <br /> <br />
          
### client_test.py - test client application, calls api functions 
- Setup: 
  - Loads companies data from file (q2_clientData.csv) containing website information;
  - Prepares and transform data;<br />

- API Test:
  - Update companies website calling the API:
    - Iterates over dataframe with companies names, zipcodes and websites ;
    - For each company tries to update data, calling HTTP Request PUT method over url http://127.0.0.1:5000/company ;
    - In each HTTP Request PUT, send a JSON content containing company_name, zipcode and website ; 
  
  - Requests companies information calling the API:
      - Iterates over dataframe with companies;
      - Call API using HTTP GET request sending JSON content with company_name and zip_code;
      - Prints received information from companies; <br />
<br /> <br />
### Testing API with HTTP Clients - Imnsonia
- GET Method: Retrieve company by name and zipcode <br />
  ![Imnsonia Test GET company](Imnsonia_GET_Test.png?raw=true "GET")
<br/> <br />
- PUT Method: Update company website information
  ![Imnsonia Test PUT company](Imnsonia_PUT_Test.png?raw=true "GET")
<br />





