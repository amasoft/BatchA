Endpoints
1. Create a Bank Receipt
Create a new bank receipt based on the provided data.

Endpoint: POST /api/bank-receipt
Request Parameters:

account_number (string, required): The recipient's bank account number.
amount (float, required): The transaction amount.
currency (string, required): The currency of the transaction (e.g., USD, EUR).
date (string, required): The date of the transaction in ISO 8601 format (e.g., "2023-11-02").
payer_name (string, required): The name of the payer.
transaction_id (string, required): A unique identifier for the transaction.
Response:

receipt_id (string): A unique identifier for the generated bank receipt.
url (string): A URL to download the bank receipt as a PDF file.
Example Request:

http
Copy code
POST /api/bank-receipt
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json

{
  account_number: "1234567890",
  amount: 100.00,
  currency: "USD",
  date: "2023-11-02",
  payer_name: "John Doe",
  transaction_id: "TX12345"
}
Example Response:

json
Copy code
{
  "receipt_id": "RECEIPT-123",
  "url": "https://example.com/receipts/RECEIPT-123.pdf"
}
Error Response:

400 Bad Request: If the request is invalid or missing required parameters.
2. Get Bank Receipt
Retrieve an existing bank receipt by its unique receipt_id.

Endpoint: GET /api/bank-receipt/{receipt_id}
Response:

receipt_id (string): A unique identifier for the bank receipt.
account_number (string): The recipient's bank account number.
amount (float): The transaction amount.
currency (string): The currency of the transaction.
date (string): The date of the transaction in ISO 8601 format.
payer_name (string): The name of the payer.
transaction_id (string): A unique identifier for the transaction.
url (string): A URL to download the bank receipt as a PDF file.
Example Request:

http
Copy code
GET /api/bank-receipt/RECEIPT-123
Authorization: Bearer YOUR_API_KEY
Example Response:

json
Copy code
{
  "receipt_id": "RECEIPT-123",
  "account_number": "1234567890",
  "amount": 100.00,
  "currency": "USD",
  "date": "2023-11-02",
  "payer_name": "John Doe",
  "transaction_id": "TX12345",
  "url": "https://example.com/receipts/RECEIPT-123.pdf"
}
Error Response:

401 Unauthorized: If the API key is missing or invalid.
404 Not Found: If the requested receipt does not exist.
3. List Bank Receipts
Retrieve a list of all bank receipts created using the API.

Endpoint: GET /api/bank-receipts
Response:

An array of bank receipt objects, each containing the following information:

receipt_id (string): A unique identifier for the bank receipt.
account_number (string): The recipient's bank account number.
amount (float): The transaction amount.
currency (string): The currency of the transaction.
date (string): The date of the transaction in ISO 8601 format.
payer_name (string): The name of the payer.
transaction_id (string): A unique identifier for the transaction.
url (string): A URL to download the bank receipt as a PDF file.
Example Request:

http
Copy code
GET /api/bank-receipts
Authorization: Bearer YOUR_API_KEY
Example Response:

json
Copy code
[
  {
    "receipt_id": "RECEIPT-123",
    "account_number": "1234567890",
    "amount": 100.00,
    "currency": "USD",
    "date": "2023-11-02",
    "payer_name": "John Doe",
    "transaction_id": "TX12345",
    "url": "https://example.com/receipts/RECEIPT-123.pdf"
  },
  {
    "receipt_id": "RECEIPT-124",
    "account_number": "9876543210",
    "amount": 50.00,
    "currency": "EUR",
    "date": "2023-11-03",
    "payer_name": "Jane Smith",
    "transaction_id": "TX67890",
    "url": "https://example.com/receipts/RECEIPT-124.pdf"
  }
]
Error Response:

401 Unauthorized: If the API key is missing or invalid.
500 Internal Server Error: If an unexpected server error occurs.
Conclusion
The Bank Receipt Printing API allows you to generate and manage bank receipts for various financial transactions. If you have any questions or encounter any issues, please contact your bank's API provider for assistance.

Thank you for using the Bank Receipt Printing API!
