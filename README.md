Objective
The goal was to build a PDF parser that can extract 5 key data points from credit card statements across 5 major credit card issuers (Citibank, American Express, Axis, SBI, HDFC).

The 5 data points chosen are:

Card Issuer (e.g., "Citibank")

Last 4 Digits of the card number

Statement Period (e.g., "18 May 2018 to 17 June 2018")

Payment Due Date (e.g., "04/07/18")

Total Balance Due (e.g., "Rs.15344.60")

Tech Stack
HTML5: For the structure of the web page.

Tailwind CSS: For all styling, providing a clean, modern UI.

JavaScript (ES6+): For all application logic, file handling, and DOM manipulation.

PDF.js (v2.16.105): A JavaScript library by Mozilla used to load and extract raw text content from PDF files directly in the browser.

Regular Expressions (Regex): This is the core "engine" of the parser. A bank of regex patterns is used to find and extract the specific data points from the raw text.

How It Works
File Upload: The user selects a PDF file using the file input.

PDF Reading (PDF.js): The file is read into an ArrayBuffer. PDF.js then loads this data, processes the PDF structure, and extracts the raw text content from all pages.

Text Normalization: The extracted text, which is often messy, is normalized by removing extra whitespace.

Parsing (Regex): The normalized text is passed to the parseStatement function.

Issuer Identification: The text is first checked against a list of keywords (Citi, HDFC, etc.) to identify the bank.

Data Extraction: A findMatch helper function iterates through an array of pre-defined regular expressions for each data point (e.g., last4Patterns, balancePatterns).

Handling Formats: These pattern arrays contain multiple regex rules to account for the different ways each bank formats its data (e.g., "Total Amount Due:" vs. "New Balance").

Display Results: The extracted data (or "Not Found") is displayed to the user in the results panel.

Challenges & Limitations
This project highlights the core difficulty of working with "unstructured" data:

Format Brittleness: The parser is 100% dependent on the regex rules. If a bank changes its statement layout even slightly (e.g., changing "Due Date:" to "Pay By:"), the parser will break for that field.

Bank-Specific Rules: The tool is not universal. It only works for the 5 banks for which specific rules have been written. Adding a new bank (e.g., Barclays) would require getting a sample statement and writing new regex patterns.

Scanned PDFs: This tool will not work on scanned (image-based) PDFs, as they contain no extractable text, only pictures of text. It requires digital-native PDFs (the kind you download directly from your bank).
