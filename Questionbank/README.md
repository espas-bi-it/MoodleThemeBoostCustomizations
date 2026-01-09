## Moodle Question Export & Import (XML)

This guide explains how to export questions from Moodle as **Moodle XML** and how to import them into any course.  
No question categories are required or used.

---

## Exporting Questions as Moodle XML

### Prerequisites
- You have access to a Moodle course containing the questions
- Editing rights in the course

### Steps

1. Open the Moodle course that contains the questions  
   *(e.g. “Aufgaben XY” or any working course)*

2. Go to  
   **Kursnavigation → Fragensammlung → Fragen**

3. (Optional)  
   If filters are active, make sure **all questions** you want to export are visible.

4. Select the questions to export  
   - Either select individual questions  
   - Or use **Select all**

5. From the **With selected** dropdown, choose:  
   **Export**

6. Choose **Moodle XML format**

7. Click **Fragen in Datei exportieren**

8. Save the generated `.xml` file locally  
   *(e.g. `questions-demo.xml`)*

✅ The Moodle XML file now contains all selected questions.

---

## Importing Questions into a Course

### Important Notes
- No question categories are created during import
- Questions are imported into the **Standard Fragensammlung** of the target course
- You can import into **any course** (e.g. “Aufgaben XY”)

---

### Steps

1. Open the target Moodle course  
   *(e.g. “Aufgaben XY”)*

2. Go to  
   **Kursnavigation → Fragensammlung → Import**

3. Choose **Moodle XML format**

4. Upload the previously exported `.xml` file

5. Import options:
   - Leave category settings unchanged  
   - Do **not** create or select additional categories

6. Click **Import**

7. Wait for the confirmation message

✅ The questions are now available in the course question bank.

---

## Using Imported Questions

After importing, you can:

- Add the questions to an existing quiz
- Create a new quiz and select the imported questions
- Edit questions directly in the question bank if needed

---

## Troubleshooting

### Imported questions are not visible
- Check **Fragensammlung → Fragen**
- Ensure no filters are active
- Verify you are in the correct course

### Import fails
- Confirm the file format is **Moodle XML**
- Re-export the questions if necessary
- Check for upload size limits

### Categories appear unexpectedly
- Moodle may assign questions to the default category automatically
- No manual category management is required

---

## Best Practice

- Keep a dedicated **working course** (e.g. “Aufgaben XY”) for imports
- Store XML files in version control (e.g. GitHub)
- Avoid unnecessary question categories for portability
- Reuse the same XML files across multiple courses when needed
