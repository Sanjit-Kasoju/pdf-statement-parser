# Credit Card Statement Parser

A single-page, client-side web app to parse PDF credit card statements. This project uses JavaScript, `PDF.js`, and Regular Expressions to extract key data entirely in the browser.

**Live Demo:** Run `statement_parser.html` in any modern web browser.

## Objective

Extract 5 key data points from statements issued by 5 major banks (Citibank, American Express, Axis, SBI, HDFC).
* **Data Points:** Card Issuer, Last 4 Digits, Statement Period, Payment Due Date, Total Balance Due.

## Tech Stack

* **JavaScript (ES6+):** Core application logic.
* **PDF.js:** Extracts raw text from PDF files.
* **Regular Expressions (Regex):** The core "engine" used to find and extract data.
* **HTML5 & Tailwind CSS:** Structure and styling.

## How It Works

1.  **File Upload:** User selects a digital PDF statement.
2.  **Text Extraction:** `PDF.js` reads the PDF and extracts its raw text content.
3.  **Parsing (Regex):** Pre-defined regex patterns are run against the text to identify the bank and find each data point.
4.  **Display:** Extracted data (or "Not Found") is shown to the user.

## Limitations

* **Format Brittleness:** Relies on regex rules. If a bank changes its statement layout, the parser will break.
* **Bank-Specific:** Only works for the 5 banks for which rules have been written.
* **No Scanned PDFs:** Cannot read scanned (image-based) PDFs, only digital-native files.

## Future Improvements

* **OCR Support:** Integrate `Tesseract.js` to read scanned PDFs.
* **Machine Learning:** Train a Named Entity Recognition (NER) model for a more robust and universal solution.
