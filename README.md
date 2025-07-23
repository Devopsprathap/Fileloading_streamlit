# Fileloading_streamlit


🧾 Summary:
This Streamlit app allows users to upload CSV or Excel files and insert, upsert, or update data into Snowflake tables. It provides options to select or create a database, schema, and table, and allows handling existing tables with different write modes including append, truncate, delete, and upsert using user-selected key columns.

🔑 Key Points:
1. Snowflake Connection
Uses snowflake.snowpark.Session.builder.getOrCreate() to initialize a session.

Validates connection by showing the current user.

2. Database & Schema Selection
Users can:

Select from existing databases/schemas.

Create a new database or schema if needed.

3. Table Selection/Creation
Existing tables are fetched for the selected schema.

User can choose an existing table or specify a new one to be created.

4. File Upload
Supports CSV and Excel files.

Includes support for custom delimiters (,, ;, \t, |, or user-defined).

5. Table Operation Options
If the table exists, users can choose:

✅ Append

🔄 Truncate and Insert

❌ Delete All and Insert

🔁 Upsert (new logic)

🚫 Cancel

6. Upsert Logic
Prompts user to select key columns.

Uses a temporary staging table to hold new data.

Executes a MERGE statement:

Matches records by key columns.

Updates matched rows and inserts unmatched ones.

Drops the staging table after completion.

7. Data Upload
For new tables: infers column types from the uploaded DataFrame and creates the table.

Uses session.write_pandas() to write data to Snowflake.

8. Error Handling
All logic wrapped in a try-except block.

Displays user-friendly error messages on failure.

Let me know if you want to extend it further with features like:

Column mapping

Data type override

Row preview filtering

Support for partitioned uploads or very large files


