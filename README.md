AI Receipt and Invoice Reader (n8n)

An n8n workflow that turns a photo of a receipt or invoice into a row in a Google Sheet. A user uploads the image through a form, AI reads it, picks out the key details, and the details are saved automatically.

What it does
A user uploads a receipt or invoice image (JPG or PNG) through a form.
An AI vision step reads the picture and writes out the text it can see.
A second AI step picks out five fields: vendor, date, total, currency and category.
The details are saved as a new row in a Google Sheet.

Splitting the work into reading and organising keeps each step simple and easier to fix.

Workflow
Receipt Form (upload)
Read Receipt (AI vision)
Pick Out Fields (AI extractor)
Save to Sheet
<!-- Add a screenshot of your workflow here: ![Workflow](docs/workflow.png) -->
Tech stack
n8n (form trigger with file upload)
OpenAI (image analysis and Information Extractor)
Google Sheets
Extracted fields
Field	Description
vendor	Shop or company name
date	Date in YYYY-MM-DD format
total	Final amount as a number
currency	For example NGN, USD or GBP
category	One of: Food, Transport, Office, Utilities, Other
Setup
In n8n, import workflow/receipt-invoice-reader.json.
Create a Google Sheet with these headings in row 1: Logged At, Receipt Date, Vendor, Total, Currency, Category, Submitted By
Choose your credentials (OpenAI, Google Sheets) on each node that shows a warning.
In Save to Sheet, select your spreadsheet.
In Read Receipt, make sure the input data field name matches the file field name on the Binary tab of the form output (the form field is called Receipt).
Execute the workflow, open the form link, and upload a file from sample-data/.
Sample data

sample-data/ has three fictional images: a clear shop receipt, an invoice with a subtotal, tax and total due, and a tilted lower-quality fuel receipt. They contain no real businesses or people.

Limitations and good practice
AI can misread blurry or dark photos. Spot-check results, especially totals and dates.
The prompt tells the AI not to guess and to write UNREADABLE or unknown when unsure.
Receipts can contain personal data. Only upload receipts you may share, and keep the original photo as the record.
Images only (JPG, PNG). PDF invoices need an extra step.
For accounting use, add a person to approve rows, especially large amounts.
Possible improvements
Alert by email when a total is above a limit
Human approval before saving
PDF invoice support
A monthly summary by category
Author

Built by Amarachi Confidence Owoh. Connect on LinkedIn.
