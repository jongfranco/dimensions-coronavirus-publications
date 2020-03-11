# dimensions-coronavirus-publications
Dimensions, from Digital Science, are maintaing a spreadsheet of all COVID-19 related papers, datasets and clinical trials:

https://docs.google.com/spreadsheets/d/1-kTZJZ1GAhJ2m4GAIhw1ZdlgO46JpvX0ZQa232VWRmw/edit#gid=1470772867

This repository contains the JSON output from processing each DOI in this spreadsheet through the [Scholarcy API](https://sandbox-api.scholarcy.com/api/). Each DOI resolves either in a PDF (if open access), an abstract, a paywalled log-in page or a cookie notice! I have no way to determine which will be the case in advance, so the data is presented in its raw form. However, I have removed files below 1K in size, as these are stubs that typically identify unprocessable files.

The JSON data structure is described in the table below:

| Field                                      | Description                                                                                                                                                                                                                                                                                                         |
|--------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| filename                                   | The filename of the uploaded document                                                                                                                                                                                                                                                                               |
| content_type                               | The file MIME type                                                                                                                                                                                                                                                                                                  |
| metadata                                   | Structured article metadata                                                                                                                                                                                                                                                                                         |
|     title                                  | Article title                                                                                                                                                                                                                                                                                                       |
|     author                                 | List of authors                                                                                                                                                                                                                                                                                                     |
|     date                                   | Article date                                                                                                                                                                                                                                                                                                        |
|     affiliations                           | Author affiliations                                                                                                                                                                                                                                                                                                 |
|     identifiers                            | Any identifier extracted from the document, such as DOI, ISBN, arXiv ID, or other identifier                                                                                                                                                                                                                        |
|     abstract                               | The original abstract, written by the author                                                                                                                                                                                                                                                                        |
|     references                             | The plain reference strings extracted from the end of the article, or from the footnotes                                                                                                                                                                                                                            |
| emails                                     | Email addresses of the authors                                                                                                                                                                                                                                                                                      |
| links                                      | Any URLs identified in the document                                                                                                                                                                                                                                                                                 |
| author_conclusions                         | Free text conclusions stated in the document                                                                                                                                                                                                                                                                        |
| table_captions                             | Table captions                                                                                                                                                                                                                                                                                                      |
| figure_captions                            | Figure captions                                                                                                                                                                                                                                                                                                     |
|                                            |                                                                                                                                                                                                                                                                                                                     |
| sections                                   | Snippets from each main section in the article                                                                                                                                                                                                                                                                      |
| introduction, methods, results, conclusion | If section headings can be mapped to standard names such as Introduction, Methods, Results, Conclusions, these snippets are shown here                                                                                                                                                                              |
|     funding                                | Any funding statements                                                                                                                                                                                                                                                                                              |
|     disclosures                            | Any disclosures of conflicts of interest                                                                                                                                                                                                                                                                            |
|     ethical_compliance                     | Any information about consent and ethical regulations                                                                                                                                                                                                                                                               |
|     data_availability                      | Any information about data and code availability related to this study                                                                                                                                                                                                                                              |
|                                            |                                                                                                                                                                                                                                                                                                                     |
| structured_content                         | The actual headings and their full section content.                                                                                                                                                                                                                                                                 |
| participants                               | Quantifiable information about the study subjects, or the population background                                                                                                                                                                                                                                     |
| statistics                                 | Information about statistical tests and analysis performed in the study                                                                                                                                                                                                                                             |
|                                            |                                                                                                                                                                                                                                                                                                                     |
|                                            |                                                                                                                                                                                                                                                                                                                     |
|                                            |                                                                                                                                                                                                                                                                                                                     |
|                                            |                                                                                                                                                                                                                                                                                                                     |
| keywords                                   | A combination of the author-supplied keywords, plus new keywords or key terms extracted from the document                                                                                                                                                                                                           |
| keyword_relevance                          | keywords ranked by their relevance scores                                                                                                                                                                                                                                                                           |
| species                                    | Any Latin species names detected                                                                                                                                                                                                                                                                                    |
| summary                                    | A longer (up to 400 words) summary of the entire article, which is aimed at more expert readers. This summary tends to include more technical details of the article.                                                                                                                                               |
| structured_summary                         | Only populated by the /metadata/extract and /highlights/extract endpoints                                                                                                                                                                                                                                           |
| reference_links                            | This is only populated by the /metadata/extract and /highlights/extract endpoints if reference parsing has been enabled. This contains links to the full text for each of the references in the paper (only output if you select this option in the API)                                                            |
| facts                                      | Subject-predicate-object facts expressed in the article                                                                                                                                                                                                                                                             |
| claims                                     | Claims made by the authors of the study                                                                                                                                                                                                                                                                             |
| findings                                   | Any important, quantitative findings extracted from the document, such as statistically significant results                                                                                                                                                                                                         |
| key_statements                             | A longer set of important sentences, from which the top_statements are selected.                                                                                                                                                                                                                                    |
| top_statements                             | The top 3-7 sentences in the document, extracted and reconstructed in such a way so that they naturally flow as a short summary that is accessible to a non-expert reader. Typically, these highlights will include introductory and concluding information, as well as the main claims and findings of the article |
| headline                                   | A short, one line summary of the entire article. This headline attempts to express the main finding or main result of the paper.                                                                                                                                                                                    |
| abbreviations                              | Abbreviations and their fully spelt out names, extracted from the document                                                                                                                                                                                                                                          |

