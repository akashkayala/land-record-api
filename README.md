Land Record Summary API
A simple Node.js API that simulates the core functionality of Landeed.com:

Accepts a land record search input

Queries a MySQL database

Generates a downloadable PDF containing the land record summary

Features
Search by parcel ID, plot number, or owner name

Returns a formatted PDF file as the API response

Clean, modular code using Node.js, Express, MySQL, and PDFKit

Tech Stack
Backend: Node.js, Express.js

Database: MySQL

PDF Generation: PDFKit

Environment Variables: dotenv

Setup Instructions
1. Clone the Repository
bash
git clone https://github.com/yourusername/land-record-api.git
cd land-record-api
2. Install Dependencies
bash
npm install
3. Configure Environment Variables
Create a .env file in the root directory:

text
DB_HOST=localhost
DB_USER=your_mysql_user
DB_PASSWORD=your_mysql_password
DB_NAME=landdb
PORT=3000
4. Set Up the Database
Log in to MySQL and run:

sql
CREATE DATABASE landdb;
USE landdb;

CREATE TABLE land_records (
  id INT AUTO_INCREMENT PRIMARY KEY,
  parcel_id VARCHAR(50),
  plot_number VARCHAR(50),
  owner_name VARCHAR(100),
  location VARCHAR(100),
  area VARCHAR(50),
  registration_date DATE
);

INSERT INTO land_records (parcel_id, plot_number, owner_name, location, area, registration_date)
VALUES
  ('LND123', '45A', 'Rakesh Rao', 'Delhi', '500 sq ft', '2021-07-10'),
  ('LND124', '46B', 'Suman Singh', 'Delhi', '600 sq ft', '2022-01-15');
5. Start the Server
bash
node server.js
API Usage
Endpoint
POST /api/land-record

Request Body
json
{
  "parcel_id": "LND123"
}
or

json
{
  "owner_name": "Rakesh Rao"
}
Response
Returns a PDF file containing the land record summary.

Example cURL Command
bash
curl -X POST http://localhost:3000/api/land-record \
  -H "Content-Type: application/json" \
  -d '{"parcel_id": "LND123"}' --output land_record.pdf
Sample Output
See sample_land_record.pdf in this repository for an example of the generated PDF.

Approach & Design
The API is built with Express.js for simplicity and speed.

MySQL is used as the database to store mock land record data.

PDFKit generates a clean, readable PDF summary for each query.

Environment variables are used for all sensitive configuration.

Input is validated and errors are handled gracefully.

Author
Akash Kayala
akashkayala373@gmail.com
GitHub Profile

License
This project is for educational and demonstration purposes only.

