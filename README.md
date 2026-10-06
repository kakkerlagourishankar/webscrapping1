# Python Web Scraping and Data Processing Pipeline

## Detailed Assignment Specification

---

# 1. Assignment Overview

The objective of this assignment is to design and implement a Python-based web scraping and data-processing pipeline capable of collecting information from multiple publicly accessible web sources, processing the collected information, cleaning and standardizing it, identifying duplicate or equivalent records, validating the resulting data, and finally producing one consolidated dataset.

This assignment is intended to evaluate practical programming and problem-solving skills rather than simply testing whether a candidate can write a basic web scraper. The solution should demonstrate the ability to work with different website structures, understand HTML content, implement reusable scraping logic, handle pagination, transform heterogeneous data into a common structure, validate records, identify duplicates, handle failures, maintain useful logs, and generate a reproducible final output.

The assignment is designed as a **medium-level Python practical task**. The candidate is expected to demonstrate reasonable knowledge of Python, web scraping, data processing, error handling, code organization, documentation, and testing.

The final solution should therefore not be a single script containing all logic in one place unless that structure is clearly justified. The preferred approach is to separate source-specific scraping logic from generic processing logic such as cleaning, validation, deduplication, and output generation.

The overall process can be summarized as:

**Multiple Public Websites → Scraping → Raw Records → Cleaning → Standardization → Validation → Duplicate Detection → Consolidation → Final Dataset → Summary Report**

The final implementation should be reproducible, understandable, and sufficiently documented so that another developer or reviewer can set up the project and execute it by following the README instructions.

The assignment specifically expects the candidate to work with two public scraping practice websites:

1. **Books to Scrape**
2. **Quotes to Scrape**

The websites are intentionally different in their structure and the type of information they provide. This allows the assignment to evaluate whether the candidate can build a common data-processing pipeline instead of creating a scraper that works only for one fixed website.

The solution should collect useful information from both sources and convert that information into a standardized data model. Because the two sources do not naturally contain exactly the same fields, the implementation must decide how fields that are unavailable for a particular source should be represented. Missing fields should use appropriate null or empty values, and the candidate must not invent information that is not available from the source.

The final project should also preserve the original source and source URL information. This is important because a consolidated dataset without traceability would make it difficult to verify where individual records came from.

The complete assignment therefore tests several related skills:

* Python programming
* Web scraping
* HTML parsing
* Pagination
* Data extraction
* Data cleaning
* Data normalization
* Data validation
* Duplicate detection
* Error handling
* Logging
* File generation
* Project structure
* Documentation
* Testing
* AI-assisted development
* Technical explanation and understanding

The candidate should focus on producing a clean and practical implementation rather than unnecessarily building a large production-scale scraping platform.

---

# 2. Assignment Scenario

You are working as a **Python Data Scraper** responsible for collecting information from multiple public websites.

Each website presents information using a different HTML structure and may use different names, formats, or arrangements for similar concepts. Your responsibility is to create a reusable process that can:

1. Access the public websites.
2. Navigate through their available pages.
3. Extract relevant information.
4. Convert the extracted information into structured Python records.
5. Clean inconsistent or unnecessary values.
6. Normalize the records into a common structure.
7. Validate the records.
8. Identify duplicate or equivalent records.
9. Preserve source information.
10. Consolidate records from multiple sources.
11. Produce a final dataset.
12. Produce a summary report describing what happened during execution.

The expected high-level workflow is:

**Website A + Website B**

↓

**Scraping**

↓

**Raw Data**

↓

**Cleaning and Standardization**

↓

**Validation**

↓

**Deduplication**

↓

**Consolidation**

↓

**Final Dataset**

↓

**Summary Report**

The important point is that the project should not treat each website as an isolated task. The final output must be a unified dataset that follows a consistent schema.

The two websites may contain different types of records. Therefore, the implementation must be flexible enough to represent both types of data while preserving the information that is actually available from each source.

For example, one source may provide a book title, category, price, rating, and availability, while the other may provide a quote, author, and tags. The standardized structure should be capable of holding these different attributes without creating false information.

The assignment also evaluates reliability. If one page fails because of a timeout, an HTTP error, or an unexpected HTML structure, the complete process should not unnecessarily terminate. The scraper should handle failures appropriately and continue processing other pages or sources whenever reasonably possible.

Logging should provide enough information for a reviewer to understand the execution process and identify problems.

The final implementation should also be understandable to another developer. This means that source-specific selectors, processing functions, validation rules, and deduplication rules should be reasonably organized and documented.

---

# 3. Data Sources

The assignment requires the use of the following public scraping practice websites.

## 3.1 Source 1 — Books to Scrape

**Website:** https://books.toscrape.com/

Books to Scrape is a practice website containing book records distributed across multiple pages.

The website provides information such as:

* Book title
* Price
* Availability
* Rating
* Category
* Product URL

The candidate should inspect the website and determine how these values are represented in the HTML.

The scraper should not simply collect a few hard-coded books. It should implement pagination so that multiple pages can be processed automatically.

The implementation should identify the appropriate page-navigation mechanism and continue through the available pages without requiring the developer to manually specify every page URL.

The extracted book records should eventually be converted into the common standardized schema used by the project.

---

## 3.2 Source 2 — Quotes to Scrape

**Website:** https://quotes.toscrape.com/

Quotes to Scrape is another public scraping practice website.

The website contains information such as:

* Quotes
* Authors
* Tags
* Author-related information

The information is distributed across multiple pages.

The candidate should inspect the HTML structure of the website and determine how the required information can be extracted.

As with Books to Scrape, pagination must be handled automatically.

The quote records should then be converted into the same standardized output structure used for the overall dataset.

Because the two sources have different structures and different types of information, the project should clearly separate the source-specific extraction logic.

---

## 3.3 Important Scraping Restrictions

The websites are public scraping practice websites. The candidate must use them only as publicly accessible sources.

The implementation must not attempt to:

* Bypass authentication
* Bypass CAPTCHAs
* Circumvent access controls
* Bypass robots or security restrictions
* Defeat security mechanisms
* Use unauthorized credentials
* Use private or restricted information

The scraper should use reasonable request rates and should avoid unnecessarily aggressive traffic.

The candidate should also avoid including secrets, passwords, API keys, personal credentials, or other sensitive information in the project.

The assignment is intended to test legitimate public web scraping and data-processing practices.

---

# 4. Main Objective

The completed solution should be able to perform the complete data pipeline from source collection to final output.

At minimum, the implementation should be able to:

### 4.1 Collect Data from Both Sources

The scraper must retrieve records from both:

* Books to Scrape
* Quotes to Scrape

The solution should not be limited to one source.

Each source should have its own scraping logic while feeding records into the common processing pipeline.

---

### 4.2 Handle Pagination

The scraper must process multiple pages from each website.

Pagination should be implemented programmatically rather than by manually listing a small number of page URLs.

The scraper should determine when it has reached the end of the available pages.

This demonstrates that the candidate understands how real-world websites distribute information across pages.

---

### 4.3 Normalize Different Source Structures

The two sources have different types of information and different HTML structures.

The project should transform these different source-specific structures into a common data model.

For example, the final structure may include fields such as:

* `source`
* `source_url`
* `name_or_title`
* `category`
* `price`
* `rating`
* `author`
* `tags`
* `description`
* `scraped_at`

Not every field will be available for every source.

The implementation should represent unavailable fields using appropriate null or empty values.

The implementation must not invent values simply to fill empty fields.

---

### 4.4 Clean and Validate Data

The extracted information may contain:

* Extra whitespace
* Different text formats
* Currency symbols
* Different rating representations
* Empty values
* Unexpected formatting
* Invalid URLs
* Unexpected HTML structures

The project should contain reusable processing functions that clean and standardize these values.

---

### 4.5 Detect Duplicates

The project must include a reasonable duplicate-detection strategy.

A simple exact string comparison is not always sufficient.

For example, the following values may represent the same logical value:

```text
Example Book Title
 Example Book Title 
EXAMPLE BOOK TITLE
```

The duplicate-detection process should account for reasonable differences such as:

* Leading whitespace
* Trailing whitespace
* Repeated whitespace
* Capitalization
* Formatting differences

The exact approach must be explained in the README.

The candidate may either:

* Remove duplicates, or
* Flag duplicates

If duplicates are flagged rather than deleted, the README should explain why.

---

### 4.6 Preserve Source Information

Each final record should retain information that identifies its origin.

At minimum, the final data should make it possible to determine:

* Which source produced the record
* What the original source URL was

This provides traceability and makes it easier to verify the data.

---

### 4.7 Handle Failures

The scraper should be designed so that a failure on one page does not unnecessarily stop the entire process.

For example, if one page produces a timeout or an unexpected response, the program should handle that situation appropriately and continue with other pages or sources whenever reasonably possible.

The implementation should use appropriate exception handling and logging.

---

### 4.8 Produce a Consolidated Dataset

After scraping, cleaning, validation, and duplicate processing, all valid records should be combined into one final dataset.

The final dataset should use a consistent schema.

---

### 4.9 Produce a Summary Report

The program should produce a summary report containing useful execution metrics.

The report should make it possible to understand:

* How many records were collected from each source
* How many records remained after cleaning
* How many records failed validation
* How many duplicates were detected
* How many duplicates were removed or flagged
* How many records remained in the final dataset
* Execution time, if available

---

# 5. Technical Requirements

## 5.1 Python

The solution must be implemented using Python.

The candidate should use clean, readable Python code and should organize the project logically.

The assignment does not require an extremely complex architecture. The priority is correctness, maintainability, readability, and practical problem-solving.

---

# 6. Web Scraping Requirements

The candidate may use an appropriate scraping library or combination of libraries.

Possible choices include:

* Requests + BeautifulSoup
* Scrapy
* Playwright
* Selenium

The selected library should be appropriate for the actual requirements of the websites.

For a static practice website, a lightweight approach such as Requests and BeautifulSoup may be sufficient.

The candidate should nevertheless be able to explain why the selected approach was appropriate.

The scraper should:

1. Make HTTP requests appropriately.
2. Handle HTTP failures.
3. Parse returned HTML.
4. Locate the required elements.
5. Extract values safely.
6. Handle missing elements.
7. Process multiple pages.
8. Preserve source URLs.
9. Return structured records.

The scraper should not crash merely because an optional HTML element is missing.

---

# 7. Suggested Standardized Data Model

A common schema should be created so that information from both websites can be represented consistently.

A suggested schema is:

```text
source
source_url
name_or_title
category
price
rating
author
tags
description
scraped_at
```

The implementation may use a Python dictionary, dataclass, pandas DataFrame structure, or another suitable representation.

For example, a conceptual record could look like:

```text
{
    "source": "...",
    "source_url": "...",
    "name_or_title": "...",
    "category": "...",
    "price": "...",
    "rating": "...",
    "author": "...",
    "tags": "...",
    "description": "...",
    "scraped_at": "..."
}
```

The exact representation is left to the candidate.

---

## 7.1 Source

The `source` field should identify where the record originated.

Examples could identify:

* Books to Scrape
* Quotes to Scrape

This field is important because the final dataset combines records from multiple websites.

---

## 7.2 Source URL

The `source_url` field should contain the original URL associated with the record.

This allows a reviewer to trace the final record back to the original public source.

URLs should be normalized or validated where appropriate.

---

## 7.3 Name or Title

The `name_or_title` field provides a common text field that can represent a book title or another appropriate primary record name.

The field should be cleaned for unnecessary whitespace.

---

## 7.4 Category

Category information should be included where the source provides it.

For a source that does not provide a category, the value should be represented as null or an appropriate empty value.

The candidate must not invent a category.

---

## 7.5 Price

Where a source provides a price, the value should be converted into a numeric representation.

For example, a text value containing a currency symbol should be transformed into a numeric value where appropriate.

The transformation should be consistent.

If no price exists for a record, the field should be empty/null rather than fabricated.

---

## 7.6 Rating

Ratings should be standardized.

The candidate should inspect how the source represents ratings and convert them into a consistent form.

The resulting values should also be validated against the expected range.

---

## 7.7 Author

Author information should be included where available.

For quote records, author information is expected to be relevant.

For records without an author field, an appropriate empty/null representation should be used.

---

## 7.8 Tags

Tags should be collected where available.

The implementation should decide on a consistent representation, such as:

* A delimited string
* A list
* Another documented structure

The selected representation should be clearly documented.

---

## 7.9 Description

Description information should be included where available.

If a source does not provide a description as part of the required scraping workflow, the field may remain empty/null.

---

## 7.10 Scraped At

The `scraped_at` field should record when the record was collected.

A consistent timestamp representation should be used.

This makes the dataset more traceable and provides useful information for later analysis.

---

# 8. Data Cleaning and Standardization

Data cleaning is a major part of the assignment.

Scraped information is often not immediately suitable for analysis because web pages contain formatting, whitespace, symbols, inconsistent representations, and missing values.

The project should therefore include reusable cleaning functions.

---

## 8.1 Remove Unnecessary Whitespace

Text fields should be cleaned by removing unnecessary leading and trailing whitespace.

For example:

```text
"   Example Book   "
```

should become:

```text
"Example Book"
```

Repeated internal whitespace may also be normalized where appropriate.

The goal is to make equivalent values consistent.

---

## 8.2 Normalize Text

Text should be normalized where appropriate.

Possible normalization operations include:

* Stripping leading/trailing whitespace
* Converting repeated whitespace into a single space
* Consistent handling of capitalization where required
* Converting HTML-derived text into clean plain text

The candidate should avoid overly aggressive transformations that could destroy meaningful information.

---

## 8.3 Convert Prices to Numeric Values

Price values should be converted from scraped text into numeric values when a price exists.

For example, a value containing a currency symbol should not remain as an unprocessed string if the final schema expects a numeric price.

The implementation should also handle unexpected price formats without crashing the entire pipeline.

Invalid values should either be rejected or handled according to the documented validation strategy.

---

## 8.4 Standardize Ratings

Ratings may be represented differently in HTML.

The candidate should convert the rating into a consistent representation.

The final rating should also be checked against the expected range.

---

## 8.5 Normalize Missing Values

Not every source contains every field.

The project should use a consistent representation for missing data.

Examples include:

* `None`
* Empty string
* Another documented null representation

The important requirement is consistency.

The candidate should not insert false or guessed information.

---

## 8.6 Normalize or Validate URLs

The scraper should preserve the original source URL and ensure that it is valid-looking.

URL handling should include reasonable validation.

Clearly invalid URLs should be identified during validation.

---

## 8.7 Remove Clearly Invalid Records

Records that are clearly unusable should not enter the final dataset.

For example, a record might be invalid if it lacks essential identifying information or contains malformed required fields.

The candidate should document which conditions cause a record to be rejected.

---

## 8.8 Separate Cleaning from Scraping

Where practical, the transformation logic should remain separate from the source-specific scraping logic.

For example:

```text
Scraper
    ↓
Raw Records
    ↓
Cleaning
    ↓
Validation
    ↓
Deduplication
    ↓
Consolidation
```

This separation improves maintainability.

If the website structure changes, source-specific scraping code can be modified without rewriting all cleaning and validation logic.

---

# 9. Duplicate Detection

Duplicate detection is a required part of the assignment.

The implementation should use a repeatable and documented strategy.

Exact string comparison alone is insufficient in many situations.

For example:

```text
Example Book Title
 Example Book Title 
EXAMPLE BOOK TITLE
```

These values differ as raw strings but may represent the same logical value.

The duplicate-detection process should therefore consider normalization.

A possible conceptual process is:

```text
Original Value
      ↓
Strip whitespace
      ↓
Normalize internal whitespace
      ↓
Normalize capitalization
      ↓
Create comparison key
      ↓
Compare records
```

The exact fields used to identify duplicates should be documented.

For example, depending on the source, a candidate may use a combination of normalized identifying fields.

The candidate must explain:

* Which fields are used
* How those fields are normalized
* What makes two records equivalent
* Whether duplicates are removed or flagged
* Why the selected strategy is appropriate

The solution should also provide measurable duplicate counts.

---

# 10. Validation

The pipeline must validate records before writing the final dataset.

Validation should help ensure that the final dataset contains useful and reasonably reliable records.

The assignment provides several examples of validation checks.

---

## 10.1 Required Fields

Required fields should be present where applicable.

The candidate should determine which fields are essential for a valid record.

For example, a record may require:

* Source
* Source URL
* Primary name/title

Other fields may be optional depending on the source.

---

## 10.2 Price Validation

If a price exists, it should be numeric.

A malformed price should be identified.

The implementation should not allow invalid price strings into a numeric output field.

---

## 10.3 Rating Validation

Ratings should fall within the expected range.

Values outside the expected range should be treated as invalid.

---

## 10.4 URL Validation

URLs should be present and valid-looking.

The validation does not need to implement a full internet verification system. The objective is to identify clearly malformed or missing URLs.

---

## 10.5 Source Validation

Every record should have a recognizable source.

The final dataset should not contain records whose origin cannot be identified.

---

## 10.6 Duplicate Metrics

Duplicate counts should be measurable.

The summary report should indicate how many duplicates were detected and, where applicable, how many were removed or flagged.

---

# 11. Error Handling and Logging

The scraper should be resilient.

Common failures include:

* Connection failures
* HTTP errors
* Timeouts
* Missing HTML elements
* Unexpected data formats
* Invalid values
* Individual page failures

The implementation should use appropriate exception handling.

The goal is not to hide errors. Instead, the system should record meaningful information and continue when it is reasonably safe to do so.

---

## 11.1 Connection Failures

A website request may fail because of a network issue.

The scraper should handle the exception and record useful information in the logs.

---

## 11.2 HTTP Errors

HTTP responses should be handled appropriately.

Unexpected status codes should not silently produce invalid data.

The scraper should log the problem and continue where practical.

---

## 11.3 Timeouts

Requests should use reasonable timeout behavior.

A timeout on one page should not necessarily stop the entire pipeline.

---

## 11.4 Missing Page Elements

HTML may not contain an expected element.

The scraper should safely handle missing elements instead of immediately crashing.

Optional values should become appropriate null/empty values.

---

## 11.5 Unexpected Data Formats

Scraped values may not always follow the expected format.

The cleaning and validation layers should detect unexpected values.

---

## 11.6 Individual Page Failures

If one page fails, the scraper should attempt to continue with other pages when reasonably possible.

This is especially important when processing multiple pages.

---

## 11.7 Logging

Logging should allow a reviewer to understand what happened during execution.

Useful information may include:

* Scraper start
* Source being processed
* Page being processed
* Number of records collected
* Request failures
* Parsing failures
* Validation failures
* Duplicate counts
* Final record count
* Execution completion

The project should store sample execution logs as part of the deliverables where appropriate.

---

# 12. Required Step-by-Step Implementation

The assignment recommends the following implementation process.

---

## Step 1 — Explore the Sources

Before writing the complete scraper, inspect both websites.

Understand:

* Page structure
* HTML structure
* Pagination
* Available fields
* Differences between sources
* URL patterns
* Missing/optional elements

The observations should be documented.

The candidate should understand the website structure before creating selectors.

---

## Step 2 — Design the Data Model

Create a common output structure that can represent records from both sources.

Decide:

* Which fields are common
* Which fields are source-specific
* Which fields are optional
* How missing fields are represented
* How timestamps are represented
* How tags are represented
* How numeric fields are stored

The model should not force nonexistent information into records.

---

## Step 3 — Build Source Scrapers

Create separate scraper modules, classes, or functions for:

* Books to Scrape
* Quotes to Scrape

Source-specific selectors and parsing logic should remain isolated.

This makes the implementation easier to maintain.

For example:

```text
scrapers/
    books_scraper.py
    quotes_scraper.py
```

The exact implementation may differ, but the separation should remain clear.

---

## Step 4 — Implement Pagination

Pagination must be handled automatically.

The implementation should:

1. Start from the appropriate initial page.
2. Extract records.
3. Identify the next page.
4. Move to the next page.
5. Continue until no additional page exists.
6. Return all collected records.

The candidate should avoid manually listing every page URL.

---

## Step 5 — Create Cleaning Functions

Create reusable functions for:

* Whitespace cleanup
* Text normalization
* Numeric conversion
* URL handling
* Rating conversion
* Missing-value handling

Cleaning should be independent from source-specific scraping wherever practical.

---

## Step 6 — Add Validation

Validate records before they enter the final dataset.

Validation should identify:

* Missing required fields
* Invalid prices
* Invalid ratings
* Invalid URLs
* Unrecognized sources
* Other clearly invalid data

Validation failures should be recorded where useful.

---

## Step 7 — Implement Deduplication

Create a repeatable duplicate-identification process.

The process should use normalized values and documented fields.

The candidate should be able to explain the strategy during an interview.

---

## Step 8 — Consolidate Data

After cleaning and validation, combine the records from both sources into one standardized dataset.

Source information should be preserved.

---

## Step 9 — Add Logging and Error Handling

Add:

* Exception handling
* Meaningful logs
* Reasonable retry behavior where appropriate
* Page-level failure handling
* Source-level failure handling

The objective is reliability without unnecessary complexity.

---

## Step 10 — Generate Output

The pipeline should produce:

```text
output/
    final_dataset.csv
    summary_report.json
```

The final CSV should contain the standardized records.

The summary report should contain execution metrics.

---

## Step 11 — Test the Solution

The complete pipeline should be executed from a clean environment.

The candidate should verify:

* Installation
* Dependencies
* Scraping
* Pagination
* Cleaning
* Validation
* Deduplication
* Output generation
* Logging

Tests should be included if implemented.

---

# 13. Expected Output

The submission should produce at minimum:

```text
output/
    final_dataset.csv
    summary_report.json
```

The final dataset should contain standardized records.

Each record should contain enough information to identify:

* The source
* The original source URL

The dataset should also contain the common fields defined by the project's standardized schema where applicable.

---

# 14. Summary Report

The summary report should provide useful execution metrics.

At minimum, it should include:

### Total records collected per source

The report should indicate how many records were initially collected from each website.

### Total records after cleaning

This shows how many records remained after transformation and cleaning.

### Records rejected during validation

This shows how many records failed validation.

### Duplicate records detected

The report should provide a measurable duplicate count.

### Duplicate records removed or flagged

If duplicates are removed, the report should indicate how many were removed.

If duplicates are flagged, the report should indicate how many were flagged.

### Final record count

This should represent the number of records in the final consolidated dataset.

### Execution time

Execution time should be included if available.

---

# 15. Example Final Dataset

A conceptual final dataset can follow this structure:

```text
source | name_or_title | category | price | rating | author | tags | source_url | scraped_at
```

Example structure:

```text
Books to Scrape | ... | ... | ... | ... | ... | ... | ... | ...
Quotes to Scrape | ... | ... | ... | ... | ... | ... | ... | ...
```

The exact values should come from the actual scraping process.

The candidate should not insert fabricated values simply to make the example appear complete.

---

# 16. Recommended Project Structure

A recommended project structure is:

```text
scraping_assignment/
│
├── scrapers/
│   ├── books_scraper.py
│   └── quotes_scraper.py
│
├── processing/
│   ├── cleaning.py
│   ├── validation.py
│   └── deduplication.py
│
├── output/
│
├── logs/
│
├── tests/
│
├── main.py
│
├── requirements.txt
│
├── README.md
│
└── AI_USAGE.md
```

This structure is only a recommendation.

A different structure is acceptable if it is:

* Clean
* Logical
* Maintainable
* Properly explained

---

## 16.1 Scrapers Directory

The `scrapers` directory should contain source-specific scraping logic.

For example:

```text
books_scraper.py
quotes_scraper.py
```

Each module should be responsible for understanding the HTML structure of its source.

---

## 16.2 Processing Directory

The `processing` directory should contain generic processing logic.

Suggested modules:

```text
cleaning.py
validation.py
deduplication.py
```

This separation prevents source-specific scraping code from becoming mixed with general data-processing logic.

---

## 16.3 Output Directory

The output directory should contain generated files such as:

```text
final_dataset.csv
summary_report.json
```

---

## 16.4 Logs Directory

Execution logs should be stored here when file-based logging is used.

---

## 16.5 Tests Directory

Automated tests may be stored here.

Tests are not mandatory unless implemented, but they can improve the quality of the submission.

---

## 16.6 Main Program

The `main.py` file can orchestrate the entire workflow:

```text
Start
 ↓
Scrape Books
 ↓
Scrape Quotes
 ↓
Combine Raw Data
 ↓
Clean
 ↓
Validate
 ↓
Deduplicate
 ↓
Generate Dataset
 ↓
Generate Summary
 ↓
Finish
```

---

# 17. AI Usage

AI tools are explicitly allowed for this assignment.

Candidates may use:

* ChatGPT
* Claude
* GitHub Copilot
* Cursor
* Gemini
* Other AI coding assistants

The use of AI does not remove the candidate's responsibility for the final implementation.

The candidate must understand the code they submit.

AI may assist with several parts of the assignment.

---

## 17.1 Understanding HTML and Page Structure

AI can be used to help understand:

* HTML structure
* CSS selectors
* XPath
* Pagination patterns
* Element extraction

However, the candidate should verify the generated suggestions against the actual website.

---

## 17.2 Generating Initial Code

AI can be used to generate initial scraper code or helper functions.

The generated code must be reviewed.

---

## 17.3 Debugging

AI can help identify and resolve:

* Selector problems
* Python errors
* Parsing errors
* Data conversion issues
* Pagination bugs

The candidate should still understand why the correction works.

---

## 17.4 Improving Scraper Logic

AI may suggest improvements to:

* Error handling
* Retry logic
* Pagination
* Code organization
* Parsing

The candidate must test these changes.

---

## 17.5 Designing Data Models

AI may help propose a standardized schema.

The final schema should be reviewed against the assignment requirements.

---

## 17.6 Generating Tests

AI may help generate unit tests or integration tests.

The candidate should verify that the tests actually test meaningful behavior.

---

## 17.7 Documentation

AI can assist with:

* README creation
* Comments
* Documentation
* AI usage documentation

The final documentation should accurately describe what was implemented.

---

## 17.8 Finding Edge Cases

AI may help identify possible edge cases such as:

* Missing elements
* Empty values
* Invalid prices
* Invalid ratings
* Duplicate values
* HTTP failures
* Pagination termination problems

The candidate should verify which edge cases actually apply.

---

## 17.9 Refactoring

AI may be used to improve code organization and readability.

However, unnecessary complexity should be avoided.

The final implementation should remain understandable.

---

# 18. Candidate Responsibility for AI-Generated Code

AI-generated code must be reviewed, tested, and corrected where necessary.

The candidate must not submit code they cannot explain.

During an interview, the candidate may be asked:

* Why did you choose this library?
* Why did you use this selector?
* How does pagination work?
* What happens if a request fails?
* How are duplicates detected?
* Why is this field nullable?
* How is price converted?
* Why is the rating represented this way?
* What did AI generate?
* What did you change?
* Did AI produce any incorrect code?

Therefore, using AI should be treated as an assistance mechanism rather than a replacement for understanding.

---

# 19. Required AI_USAGE.md

The project must include:

```text
AI_USAGE.md
```

This file should document how AI was used during the development process.

It should include:

1. AI tools used
2. What each tool was used for
3. Representative prompts
4. Which code sections were AI-assisted
5. Changes made after reviewing AI output
6. Incorrect or incomplete AI suggestions discovered
7. How the final implementation was tested and verified

---

## 19.1 AI Tool Information

The document should identify the tools used.

For example:

```text
Tool: ChatGPT
```

---

## 19.2 Purpose

The candidate should explain what the tool was used for.

Example:

```text
Used for: Initial pagination approach and debugging a selector issue.
```

---

## 19.3 Representative Prompts

The candidate should provide a few representative prompts.

These should demonstrate the actual type of assistance requested.

---

## 19.4 AI-Assisted Code

The document should identify which parts of the code were AI-assisted.

Examples might include:

* Initial scraper structure
* Pagination logic
* Cleaning helpers
* Validation functions
* Test generation

---

## 19.5 Changes After AI Review

The candidate should explain what they changed after reviewing AI output.

This demonstrates that the candidate did not blindly accept generated code.

---

## 19.6 Incorrect AI Suggestions

If AI generated incorrect or incomplete suggestions, the candidate should document them.

This is useful because it demonstrates the ability to evaluate AI-generated code critically.

---

## 19.7 Verification

The candidate should explain how the final implementation was tested.

Example:

```text
Tool: ChatGPT
Used for: Initial pagination approach and debugging a selector issue.
Verification: Tested pagination against all available pages and manually checked sample records.
```

---

# 20. README.md Requirements

The project must include a comprehensive `README.md`.

The README should include:

* Assignment/project overview
* Python version
* Installation instructions
* Setup instructions
* Dependencies
* How to run the scraper
* Pagination explanation
* Data model
* Cleaning approach
* Validation approach
* Deduplication approach
* Error-handling approach
* Output description
* Assumptions
* Known limitations
* AI usage summary

---

## 20.1 Assignment Overview

Explain what the project does and identify the two data sources.

---

## 20.2 Python Version

Specify the Python version used during development and testing.

---

## 20.3 Installation

Explain how to create and prepare the environment.

The instructions should allow another person to reproduce the project.

---

## 20.4 Dependencies

The README should identify the libraries required by the project.

These dependencies should also be included in:

```text
requirements.txt
```

---

## 20.5 Running the Scraper

The README should clearly explain how to execute the pipeline.

A reviewer should not need to inspect the source code to understand how to start the project.

---

## 20.6 Pagination

Explain how the scraper identifies and processes subsequent pages.

---

## 20.7 Data Model

Document the standardized schema and explain the purpose of each field.

---

## 20.8 Cleaning

Explain:

* Whitespace handling
* Numeric conversion
* Rating normalization
* Missing-value handling
* URL normalization

---

## 20.9 Validation

Document the validation rules.

---

## 20.10 Deduplication

Explain:

* Duplicate fields
* Normalization
* Comparison strategy
* Removal or flagging strategy

---

## 20.11 Error Handling

Explain how the project handles:

* HTTP errors
* Connection failures
* Timeouts
* Missing elements
* Unexpected formats
* Page failures

---

## 20.12 Output

Document the generated files:

```text
output/final_dataset.csv
output/summary_report.json
```

---

## 20.13 Assumptions

Document reasonable assumptions made during development.

The candidate should not silently make assumptions that significantly affect the result.

---

## 20.14 Known Limitations

Document limitations honestly.

For example, a scraper may depend on the current HTML structure of the websites.

---

## 20.15 AI Usage Summary

Provide a short summary of how AI was used and refer to `AI_USAGE.md` for more details.

---

# 21. Deliverables

The final submission should be provided as **one ZIP file**.

The ZIP should contain:

```text
Complete Python source code
requirements.txt
README.md
AI_USAGE.md
Final consolidated dataset
Summary report
Sample execution logs
Tests, if implemented
Configuration files, if used
```

The submission should be clean and organized.

Temporary files, unnecessary generated artifacts, credentials, passwords, and API keys should not be included.

---

# 22. Bonus Features

The following features are optional and may provide additional credit.

They should not be implemented at the expense of the required functionality.

---

## 22.1 MongoDB or PostgreSQL Integration

The final or intermediate data may optionally be stored in a database such as:

* MongoDB
* PostgreSQL

The core CSV output should still satisfy the required deliverable.

---

## 22.2 Retry Mechanism with Exponential Backoff

The scraper may implement retries for temporary failures.

An exponential backoff strategy can prevent excessive repeated requests.

---

## 22.3 Configurable Settings

The scraper may use configuration options for values such as:

* URLs
* Request timeout
* Retry count
* Output paths
* Logging level

The implementation should remain easy to understand.

---

## 22.4 Unit Tests

Automated tests can be added for:

* Cleaning
* Validation
* Deduplication
* Parsing
* Utility functions

---

## 22.5 Parallel or Asynchronous Processing

The project may optionally process sources or pages concurrently.

However, concurrency should be used responsibly.

The candidate should avoid aggressive traffic and should respect reasonable request rates.

---

## 22.6 Rate Limiting

The scraper may deliberately limit request frequency.

This can improve responsible scraping behavior.

---

## 22.7 Incremental Scraping

An incremental scraper could avoid unnecessarily reprocessing records already collected.

This is an optional enhancement.

---

## 22.8 Checkpoint and Resume

The scraper could save progress and resume after an interruption.

This is particularly useful for larger scraping jobs, although it is not required for the basic assignment.

---

## 22.9 Docker Setup

The project may optionally include a Docker configuration.

The objective would be to make the environment reproducible.

---

## 22.10 Data Quality Report

An additional report could provide information about:

* Missing fields
* Invalid values
* Duplicate rates
* Records per source
* Validation failures

---

## 22.11 CLI Arguments

The scraper may support command-line arguments for controlling execution.

Possible controls could include:

* Source selection
* Output location
* Logging level
* Retry settings
* Other documented configuration

---

# 23. Evaluation Criteria

The assignment will be evaluated using the following categories:

| Evaluation Area                   | Weight |
| --------------------------------- | -----: |
| Python & Code Quality             |    20% |
| Web Scraping                      |    20% |
| Data Cleaning & Standardization   |    15% |
| Duplicate Detection               |    15% |
| Error Handling & Reliability      |    10% |
| Documentation & Project Structure |    10% |
| AI Usage & Understanding          |    10% |

Total:

**100%**

---

## 23.1 Python and Code Quality — 20%

The reviewer will evaluate:

* Python correctness
* Readability
* Organization
* Naming
* Maintainability
* Separation of responsibilities
* Reasonable use of functions/classes
* Avoidance of unnecessary complexity

The code should be understandable to another developer.

---

## 23.2 Web Scraping — 20%

The reviewer will evaluate:

* Correct extraction
* Multiple-page scraping
* Pagination
* Source-specific parsing
* Missing-element handling
* URL preservation

---

## 23.3 Data Cleaning and Standardization — 15%

The reviewer will evaluate:

* Whitespace cleaning
* Numeric conversion
* Rating normalization
* Missing values
* URL handling
* Standardized schema
* Separation of cleaning from scraping

---

## 23.4 Duplicate Detection — 15%

The reviewer will evaluate:

* Duplicate strategy
* Normalization
* Repeatability
* Correct duplicate identification
* Documentation
* Duplicate metrics

---

## 23.5 Error Handling and Reliability — 10%

The reviewer will evaluate:

* Exception handling
* HTTP failure handling
* Timeout handling
* Missing-element handling
* Page-level failures
* Logging
* Ability to continue where reasonably possible

---

## 23.6 Documentation and Project Structure — 10%

The reviewer will evaluate:

* README quality
* Setup instructions
* Project organization
* Data-model explanation
* Cleaning explanation
* Validation explanation
* Deduplication explanation
* Output documentation
* Assumptions
* Limitations

---

## 23.7 AI Usage and Understanding — 10%

The reviewer will evaluate:

* Transparency about AI use
* Quality of AI_USAGE.md
* Understanding of AI-generated code
* Ability to explain implementation
* Evidence of testing and verification
* Awareness of incorrect AI suggestions

---

# 24. Interview Follow-Up

After submission, the candidate may be asked to walk through the project.

The purpose of the interview is to determine whether the candidate genuinely understands the implementation.

The candidate should be prepared to explain the complete pipeline.

---

## 24.1 Why Did You Choose Your Scraping Library?

The candidate should explain the reasoning behind the chosen library.

The answer should relate to the actual characteristics of the websites and the requirements of the assignment.

---

## 24.2 How Does Pagination Work?

The candidate should explain:

1. How the first page is loaded
2. How records are extracted
3. How the next page is identified
4. How the scraper determines when pagination ends
5. How page failures are handled

---

## 24.3 How Did You Handle Missing Fields?

The candidate should explain the difference between:

* Required fields
* Optional fields
* Source-specific fields

They should explain how unavailable information is represented without inventing data.

---

## 24.4 How Did You Handle Failed Requests?

The candidate should be able to explain:

* HTTP error handling
* Timeouts
* Connection errors
* Retry behavior if implemented
* Logging
* Continuing with other pages

---

## 24.5 How Does Duplicate Detection Work?

The candidate should explain:

* Which fields are compared
* How values are normalized
* How comparison keys are created
* How duplicates are detected
* Whether duplicates are removed or flagged

---

## 24.6 Why Did You Choose Your Standardized Schema?

The candidate should explain how the schema accommodates both websites.

They should also explain how source-specific information is handled.

---

## 24.7 What Assumptions Did You Make?

The candidate should identify important assumptions rather than pretending that none were made.

Examples could include assumptions related to:

* Valid values
* Optional fields
* Rating ranges
* Duplicate definitions
* URL structure

---

## 24.8 Which Parts Were AI-Assisted?

The candidate should be able to clearly identify where AI helped.

The answer should match the contents of `AI_USAGE.md`.

---

## 24.9 Did AI-Generated Code Create Any Problems?

The candidate should be prepared to discuss incorrect or incomplete AI-generated suggestions.

This is an important part of demonstrating practical AI-assisted development skills.

---

## 24.10 How Did You Verify the Final Result?

The candidate should explain:

* Manual checks
* Automated tests
* Sample records
* Pagination verification
* Output validation
* Duplicate checks
* Error-handling tests

---

## 24.11 What Would You Change for Production?

The candidate may be asked how the project could be improved if it needed to run regularly in a production environment.

Possible areas of discussion include:

* Monitoring
* Better retry handling
* Rate limiting
* Database storage
* Incremental scraping
* Checkpointing
* Configuration
* Automated tests
* Deployment
* Data-quality monitoring
* Alerting

The candidate should distinguish between what is required for this medium-level assignment and what would be appropriate for a larger production system.

---

# 25. Important Rules

The following rules must be followed.

### Rule 1 — Public Information Only

Use only publicly accessible information from the provided practice websites.

---

### Rule 2 — Do Not Bypass Security

Do not bypass:

* Authentication
* CAPTCHA
* Access controls
* Security mechanisms
* Other restrictions

---

### Rule 3 — Reasonable Request Rates

Respect reasonable request rates.

Avoid unnecessarily aggressive traffic.

The assignment is intended to demonstrate responsible web scraping.

---

### Rule 4 — No Secrets

Do not include:

* API keys
* Passwords
* Credentials
* Private tokens
* Other secrets

in the submission.

---

### Rule 5 — AI Is Allowed

AI usage is explicitly permitted.

However, the candidate must understand and be able to explain the submitted implementation.

---

### Rule 6 — Reproducibility

The final submission should be reproducible using the instructions provided in the README.

A reviewer should be able to:

1. Set up the environment.
2. Install dependencies.
3. Run the program.
4. Produce the expected outputs.

---

# 26. Expected Level

This assignment is classified as a **medium-level Python assignment**.

The candidate is not expected to build a large production scraping platform.

The primary focus is on practical engineering skills.

The solution should demonstrate that the candidate can:

* Write clean Python
* Understand HTML
* Scrape multiple sources
* Handle different data structures
* Implement pagination
* Extract structured information
* Clean data
* Standardize records
* Validate records
* Detect duplicates
* Handle failures
* Log meaningful events
* Consolidate information
* Generate output files
* Document the project
* Use AI responsibly
* Explain the final implementation

The assignment is not primarily about using the most advanced scraping framework.

A simple, reliable, well-organized implementation can be stronger than an unnecessarily complicated solution.

The candidate should therefore prioritize:

**Correctness → Reliability → Clarity → Maintainability → Documentation**

rather than adding unnecessary technology.

---

# 27. Complete End-to-End Pipeline

The complete solution should conceptually follow this sequence:

```text
                 ┌──────────────────────┐
                 │   Books to Scrape    │
                 └──────────┬───────────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ Books Scraper │
                    └───────┬───────┘
                            │
                            │
                            ▼
                    ┌───────────────┐
                    │   Raw Books   │
                    │    Records    │
                    └───────┬───────┘
                            │
                            │
┌──────────────────────┐    │
│  Quotes to Scrape    │    │
└──────────┬───────────┘    │
           │                │
           ▼                │
   ┌───────────────┐       │
   │Quotes Scraper │       │
   └───────┬───────┘       │
           │               │
           ▼               │
   ┌───────────────┐       │
   │ Raw Quotes    │       │
   │    Records    │       │
   └───────┬───────┘       │
           │               │
           └───────┬───────┘
                   ▼
          ┌─────────────────┐
          │  Consolidation  │
          │  of Raw Records │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ Data Cleaning   │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ Standardization │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │   Validation    │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │  Deduplication  │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ Final Dataset   │
          └────────┬────────┘
                   │
          ┌────────┴─────────┐
          ▼                  ▼
 ┌─────────────────┐  ┌─────────────────┐
 │ final_dataset   │  │ summary_report  │
 │     .csv        │  │      .json      │
 └─────────────────┘  └─────────────────┘
```

This architecture demonstrates the main purpose of the assignment: transforming heterogeneous public web information into one clean, validated, traceable dataset.

---

# 28. Recommended Development Approach

A practical implementation can be developed incrementally.

First, inspect the two websites and understand their structures.

Second, create a small working scraper for each source.

Third, verify that each scraper can process more than one page.

Fourth, convert the raw output into a common structure.

Fifth, implement reusable cleaning functions.

Sixth, implement validation.

Seventh, implement duplicate detection.

Eighth, combine all valid records.

Ninth, add logging and robust error handling.

Tenth, generate the required output files.

Finally, test the complete pipeline from a clean environment and document the implementation.

This approach reduces debugging complexity because each layer can be tested independently.

---

# 29. Quality Expectations

A strong submission should demonstrate that the candidate has thought about the entire lifecycle of scraped data rather than only the extraction step.

The scraper should not simply download HTML and write selected strings into a CSV.

A complete solution should show the following progression:

```text
Raw Website Data
        ↓
Structured Records
        ↓
Clean Records
        ↓
Validated Records
        ↓
Duplicate-Checked Records
        ↓
Consolidated Dataset
```

Every stage should have a clear responsibility.

The implementation should also preserve enough information to trace a final record back to its original source.

The candidate should avoid hard-coding a small number of pages merely to produce a working demonstration.

Similarly, the candidate should avoid silently ignoring errors.

A strong solution records meaningful failures and continues where appropriate.

---

# 30. Final Submission Checklist

Before submitting the project, the candidate should verify the following.

## Scraping

* [ ] Python is used.
* [ ] Books to Scrape is processed.
* [ ] Quotes to Scrape is processed.
* [ ] Multiple pages are processed.
* [ ] Pagination is implemented.
* [ ] Source-specific parsing is separated.
* [ ] Missing HTML elements do not unnecessarily crash the program.
* [ ] Source information is preserved.
* [ ] Original source URLs are preserved.

## Data Model

* [ ] A common schema is defined.
* [ ] Fields are documented.
* [ ] Missing fields are represented appropriately.
* [ ] No data is invented.

## Cleaning

* [ ] Whitespace is cleaned.
* [ ] Text is normalized where appropriate.
* [ ] Prices are converted to numeric values.
* [ ] Ratings are standardized.
* [ ] Missing values are normalized.
* [ ] URLs are handled appropriately.
* [ ] Clearly invalid records are removed/rejected.
* [ ] Cleaning logic is separated from scraping where practical.

## Validation

* [ ] Required fields are checked.
* [ ] Prices are validated.
* [ ] Ratings are validated.
* [ ] URLs are checked.
* [ ] Sources are validated.
* [ ] Validation failures are measurable.

## Deduplication

* [ ] A duplicate strategy is implemented.
* [ ] Normalization is considered.
* [ ] Duplicate fields are documented.
* [ ] Duplicate counts are measurable.
* [ ] Removal/flagging behavior is documented.

## Reliability

* [ ] Connection failures are handled.
* [ ] HTTP errors are handled.
* [ ] Timeouts are handled.
* [ ] Missing elements are handled.
* [ ] Unexpected formats are handled.
* [ ] Individual page failures are handled.
* [ ] Logging is implemented.

## Output

* [ ] `final_dataset.csv` is generated.
* [ ] `summary_report.json` is generated.
* [ ] Source information is present.
* [ ] Source URLs are present.
* [ ] Final records are standardized.

## Documentation

* [ ] README exists.
* [ ] Python version is documented.
* [ ] Dependencies are documented.
* [ ] Setup is documented.
* [ ] Execution instructions are documented.
* [ ] Pagination is explained.
* [ ] Data model is explained.
* [ ] Cleaning is explained.
* [ ] Validation is explained.
* [ ] Deduplication is explained.
* [ ] Error handling is explained.
* [ ] Outputs are explained.
* [ ] Assumptions are documented.
* [ ] Limitations are documented.

## AI Usage

* [ ] AI_USAGE.md exists.
* [ ] AI tools are identified.
* [ ] AI usage is described.
* [ ] Representative prompts are included.
* [ ] AI-assisted code is identified.
* [ ] Changes to AI-generated code are documented.
* [ ] Incorrect AI suggestions are documented where applicable.
* [ ] Verification/testing is documented.

## Submission

* [ ] Complete source code is included.
* [ ] `requirements.txt` is included.
* [ ] `README.md` is included.
* [ ] `AI_USAGE.md` is included.
* [ ] Final dataset is included.
* [ ] Summary report is included.
* [ ] Sample logs are included.
* [ ] Tests are included if implemented.
* [ ] Configuration files are included if required.
* [ ] No passwords, credentials, API keys, or secrets are included.
* [ ] The project can be reproduced from the README.

---

# 31. Final Understanding of the Assignment

The central requirement of this assignment is not simply to scrape two websites.

The real objective is to demonstrate the ability to build a **complete and reusable data-processing pipeline**.

The candidate starts with two different public sources:

```text
Books to Scrape
Quotes to Scrape
```

Each source has its own structure, fields, and pagination mechanism.

The candidate must therefore create source-specific scraping components.

Those components produce raw records.

The raw records then enter a common processing pipeline:

```text
Scraping
   ↓
Cleaning
   ↓
Standardization
   ↓
Validation
   ↓
Deduplication
   ↓
Consolidation
   ↓
Output
```

The final result should be a standardized dataset that preserves source information and can be traced back to the original public URLs.

The project must also provide a summary of what occurred during execution.

This includes:

* Records collected
* Records cleaned
* Records rejected
* Duplicates detected
* Duplicates removed or flagged
* Final record count
* Execution time when available

The implementation should also demonstrate practical engineering behavior.

For example, if one page fails, the scraper should not unnecessarily stop the complete process. If an element is missing, the scraper should handle it safely. If a value has an unexpected format, the processing pipeline should detect it instead of silently creating incorrect data.

The project should also be transparent about AI usage.

AI tools are permitted and can be used for many development activities, but the candidate remains responsible for the final implementation. The candidate must review, test, understand, and be able to explain the submitted code.

The README and AI_USAGE.md files are therefore important parts of the submission rather than optional documentation.

The assignment intentionally does not require a large production scraping platform. The expected level is medium.

The most important qualities are:

**Clean Python**

**Correct scraping**

**Reliable pagination**

**Good data cleaning**

**Consistent standardization**

**Reasonable duplicate detection**

**Basic validation**

**Useful error handling**

**Meaningful logging**

**Clear project structure**

**Reproducible documentation**

**Responsible AI usage**

**Ability to explain the implementation**

A simple solution that correctly implements these requirements is preferable to an unnecessarily complicated solution that introduces technologies without a clear purpose.

The final ZIP submission should therefore be organized, reproducible, and easy for a reviewer to inspect.

At a minimum, the reviewer should be able to understand:

1. What the project does.
2. Which sources it uses.
3. How each source is scraped.
4. How pagination works.
5. How raw records are standardized.
6. How data is cleaned.
7. How records are validated.
8. How duplicates are identified.
9. How errors are handled.
10. How logging works.
11. How the final dataset is generated.
12. How the summary report is generated.
13. How AI was used.
14. How the solution was tested.
15. What limitations and assumptions exist.

The assignment therefore represents a complete practical exercise in Python web scraping and data engineering fundamentals.

---

# 32. Core Requirements in One View

The complete requirement can be summarized as follows:

```text
                PUBLIC DATA SOURCES
                       │
          ┌────────────┴────────────┐
          │                         │
          ▼                         ▼
 Books to Scrape             Quotes to Scrape
          │                         │
          ▼                         ▼
 Books Scraper               Quotes Scraper
          │                         │
          └────────────┬────────────┘
                       ▼
                  RAW RECORDS
                       │
                       ▼
               DATA CLEANING
                       │
                       ▼
              STANDARDIZATION
                       │
                       ▼
                  VALIDATION
                       │
                       ▼
                DEDUPLICATION
                       │
                       ▼
                CONSOLIDATION
                       │
             ┌─────────┴─────────┐
             ▼                   ▼
     final_dataset.csv    summary_report.json
```

Alongside this pipeline:

```text
Error Handling
      +
Logging
      +
Testing
      +
Documentation
      +
AI Usage Documentation
```

must support the complete implementation.

The final project should remain faithful to the assignment's purpose: demonstrating practical Python, web scraping, data-processing, problem-solving, error handling, code-quality, and technical understanding skills at a medium level.

---

# 33. Essential Files for the Final ZIP

The expected final project can therefore contain the following:

```text
scraping_assignment/
│
├── scrapers/
│   ├── books_scraper.py
│   └── quotes_scraper.py
│
├── processing/
│   ├── cleaning.py
│   ├── validation.py
│   └── deduplication.py
│
├── output/
│   ├── final_dataset.csv
│   └── summary_report.json
│
├── logs/
│   └── sample_execution.log
│
├── tests/
│   └── ...
│
├── main.py
├── requirements.txt
├── README.md
└── AI_USAGE.md
```

The exact structure can be changed if another structure is cleaner, provided the organization and reasoning are documented.

---

# 34. Final Submission Standard

A successful submission should satisfy the required functionality without unnecessary complexity.

The reviewer should be able to run the project using the README instructions and observe that:

* Both websites are scraped.
* Pagination works.
* Data is extracted.
* Records are standardized.
* Values are cleaned.
* Invalid records are handled.
* Duplicates are detected.
* Sources and URLs are preserved.
* Errors are handled.
* Execution is logged.
* The final CSV is produced.
* The summary report is produced.
* The project documentation explains the implementation.
* AI usage is transparently documented.
* The candidate can explain the code.

The final solution should be treated as a practical software project rather than a collection of disconnected code snippets.

The strongest implementation is one where every component has a clear purpose and the complete pipeline works reliably from beginning to end.

**Primary objective:**

> Build a Python-based web scraping and data-processing pipeline that collects information from Books to Scrape and Quotes to Scrape, handles pagination, transforms both sources into a common schema, cleans and validates the data, detects duplicates, handles failures, preserves source information, and generates a final consolidated CSV together with a summary report.

That objective, together with the technical requirements, documentation requirements, AI usage requirements, deliverables, evaluation criteria, and interview expectations described above, represents the complete scope of the assignment.
