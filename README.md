# AI University Assistant

## 1. Project Overview

The **AI University Assistant** is a prototype that answers students' questions about university courses, assignments, deadlines, and learning resources. It uses the Google Gemini API to generate natural-language answers based on the project data and prompts.

The repository also contains example files, diagrams, and test cases used to document and evaluate the prototype.

> **Scope:** The current prototype uses the repository's prepared data. It does not connect to a live Moodle server unless a separate integration is implemented.

## 2. Project Objectives

- Answer common university questions in natural language.
- Use structured course, assignment, and resource data as context for Gemini.
- Keep the system instructions and evaluation prompt in separate files.
- Document the solution architecture with diagrams and examples.
- Evaluate responses using test cases with inputs (X) and expected outputs (Y).

## 3. Repository Structure

```text
AI-University-Assistant/
├── AI_University_Assistant_Gemini.ipynb
├── README.md
├── data/
│   ├── assignments.csv
│   ├── courses.csv
│   ├── resources.csv
│   └── test_cases.csv
├── diagrams/
│   └── project diagrams
├── examples/
│   └── example files
└── prompts/
    ├── system_prompt.txtx
    └── test_prompt.txt
```

The tree above summarizes the repository organization. If a filename or extension in the actual repository differs, use the exact name shown in GitHub. The prompt file currently described as `system_prompt.txtx` is written here exactly as provided; check whether the extra `x` is intentional or whether the file should be renamed to `system_prompt.txt`.

## 4. Data Files

The `data/` directory contains the information used by the prototype and its tests.

### `assignments.csv`

Contains assignment records. Depending on the current dataset schema, fields can include an assignment ID, course ID, assignment name, deadline, and status.

### `courses.csv`

Contains the available course records, such as course IDs and course names.

### `resources.csv`

Contains learning resources associated with courses, such as resource titles, types, or descriptions.

### `test_cases.csv` — X and Y pairs

The `test_cases` data contains the input/output examples used to evaluate the assistant. These are the project's **X/Y pairs**:

- **X (input):** The test question or prompt supplied to the assistant. For example: `What is the deadline for the SQL Project?`
- **Y (expected output):** The reference answer or expected information that the assistant should return. For example: `The SQL Project is due on October 12, 2026.` This is an illustrative example; the expected answer must match the actual data in the repository.

The X/Y pairs are evaluation examples. They are **not training data used to train or fine-tune Gemini** in this project. The assistant sends the question and relevant data to the Gemini API at runtime and evaluates the generated answer against the expected output.

Check the actual `test_cases` file to confirm the exact column names used for X and Y; those names may differ from `X` and `Y` (for example, `input` and `expected_output`).

## 5. Prompts

The `prompts/` directory stores prompt text separately from the Python notebook.

- **`system_prompt.txtx`** — intended to contain the assistant's general behavior instructions, such as answering from supplied data, avoiding invented details, and stating when information is unavailable. Confirm whether the `.txtx` extension is intentional.
- **`test_prompt.txt`** — intended to contain a prompt used for testing or evaluating the assistant.

Keeping prompts in separate files makes them easier to review and update without searching through all the notebook code. If the notebook currently defines prompts directly in Python, make sure any changes to these files are also reflected in the code; files are not automatically used unless the notebook reads them.

## 6. Examples and Diagrams

### `examples/`

Contains example files illustrating sample questions, prompts, interactions, or outputs. Refer to the individual files for their exact purpose and contents.

### `diagrams/`

Contains the project's diagrams, which may document the system architecture, request flow, data handling, or evaluation process. These diagrams supplement the implementation by showing how the components relate to one another.

## 7. Technologies

- **Python** — application and data-handling code.
- **Google Colab / Jupyter Notebook** — development and execution environment.
- **Google Gemini API** — natural-language response generation.
- **Google Gen AI SDK (`google-genai`)** — Python interface to Gemini.
- **Pandas** — CSV loading and processing.
- **IPyWidgets** — optional interactive controls in the notebook.
- **Matplotlib** — optional visualization of test results.
- **Git and GitHub** — version control and project collaboration.

## 8. How the System Works

1. **Load data:** The notebook loads the course, assignment, and resource datasets from `data/` (or from uploaded copies, depending on the notebook implementation).
2. **Receive a question:** The student enters a natural-language question.
3. **Retrieve context:** The code selects records relevant to the question.
4. **Build the prompt:** The question, selected context, and system instructions are assembled into the request sent to Gemini.
5. **Generate an answer:** Gemini generates a response based on the supplied context.
6. **Evaluate:** The test cases provide an input X and an expected output Y for checking the response.
7. **Review results:** Test outcomes can be inspected in the notebook and, if the notebook exports them, in a generated results file.

## 9. Running the Prototype

1. Open `AI_University_Assistant_Gemini.ipynb` in Google Colab, if that notebook is present in the repository.
2. Run the installation and import cells.
3. Provide a valid Gemini API key when prompted.
4. Load or upload the data files from `data/` as requested by the notebook.
5. Run the remaining cells in order.
6. Enter a question and inspect the generated answer.
7. Run the evaluation cells to compare responses with the test cases.

The exact steps depend on the current notebook implementation and the names of its data columns.

## 10. Evaluation and Limitations

The test cases provide reference inputs and expected outputs. Evaluation may use keyword checks or other simple comparisons. Such checks are useful for a prototype but do not fully measure factual correctness: a valid answer may use different wording, while an answer containing expected keywords may still be wrong. Review representative outputs manually.

Other current limitations may include:

- The assistant only knows the data supplied to it; it cannot verify information against a live Moodle instance.
- Retrieval quality depends on the filtering logic and the wording of the user's question.
- Gemini can produce inaccurate or incomplete answers, so responses should be checked.
- Information absent from the datasets, such as a grade that is not recorded, should be reported as unavailable rather than invented.
- API use depends on key validity, model availability, and quota.

## 11. Security

- Do not commit Gemini API keys, access tokens, passwords, or other secrets to GitHub.
- Enter the API key at runtime using a secure input mechanism.
- Do not include private student records in the repository unless authorized and appropriately protected.
- Review notebook outputs before committing them to ensure credentials or sensitive data are not exposed.

## 12. Conclusion

The AI University Assistant demonstrates a workflow for answering university-related questions using structured data, prompts, and a generative AI API. The repository separates datasets, X/Y evaluation cases, prompt files, examples, and diagrams so that each part of the prototype can be inspected and improved independently.
