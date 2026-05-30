```python
COHERE_API_KEY = "Enter Cohere API Key"
!pip install cohere
import cohere
```

    Collecting cohere
      Downloading cohere-7.0.2-py3-none-any.whl.metadata (6.9 kB)
    Collecting fastavro<2.0.0,>=1.9.4 (from cohere)
      Downloading fastavro-1.12.2-cp312-cp312-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl.metadata (5.8 kB)
    Requirement already satisfied: httpx>=0.21.2 in /usr/local/lib/python3.12/dist-packages (from cohere) (0.28.1)
    Requirement already satisfied: pydantic>=1.9.2 in /usr/local/lib/python3.12/dist-packages (from cohere) (2.12.3)
    Requirement already satisfied: pydantic-core<3.0.0,>=2.18.2 in /usr/local/lib/python3.12/dist-packages (from cohere) (2.41.4)
    Requirement already satisfied: requests<3.0.0,>=2.0.0 in /usr/local/lib/python3.12/dist-packages (from cohere) (2.32.4)
    Requirement already satisfied: tokenizers<1,>=0.15 in /usr/local/lib/python3.12/dist-packages (from cohere) (0.22.2)
    Collecting types-requests<3.0.0,>=2.0.0 (from cohere)
      Downloading types_requests-2.33.0.20260518-py3-none-any.whl.metadata (2.2 kB)
    Requirement already satisfied: typing_extensions>=4.0.0 in /usr/local/lib/python3.12/dist-packages (from cohere) (4.15.0)
    Requirement already satisfied: anyio in /usr/local/lib/python3.12/dist-packages (from httpx>=0.21.2->cohere) (4.13.0)
    Requirement already satisfied: certifi in /usr/local/lib/python3.12/dist-packages (from httpx>=0.21.2->cohere) (2026.5.20)
    Requirement already satisfied: httpcore==1.* in /usr/local/lib/python3.12/dist-packages (from httpx>=0.21.2->cohere) (1.0.9)
    Requirement already satisfied: idna in /usr/local/lib/python3.12/dist-packages (from httpx>=0.21.2->cohere) (3.15)
    Requirement already satisfied: h11>=0.16 in /usr/local/lib/python3.12/dist-packages (from httpcore==1.*->httpx>=0.21.2->cohere) (0.16.0)
    Requirement already satisfied: annotated-types>=0.6.0 in /usr/local/lib/python3.12/dist-packages (from pydantic>=1.9.2->cohere) (0.7.0)
    Requirement already satisfied: typing-inspection>=0.4.2 in /usr/local/lib/python3.12/dist-packages (from pydantic>=1.9.2->cohere) (0.4.2)
    Requirement already satisfied: charset_normalizer<4,>=2 in /usr/local/lib/python3.12/dist-packages (from requests<3.0.0,>=2.0.0->cohere) (3.4.7)
    Requirement already satisfied: urllib3<3,>=1.21.1 in /usr/local/lib/python3.12/dist-packages (from requests<3.0.0,>=2.0.0->cohere) (2.5.0)
    Requirement already satisfied: huggingface-hub<2.0,>=0.16.4 in /usr/local/lib/python3.12/dist-packages (from tokenizers<1,>=0.15->cohere) (1.16.1)
    Requirement already satisfied: filelock>=3.10.0 in /usr/local/lib/python3.12/dist-packages (from huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (3.29.0)
    Requirement already satisfied: fsspec>=2023.5.0 in /usr/local/lib/python3.12/dist-packages (from huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (2025.3.0)
    Requirement already satisfied: hf-xet<2.0.0,>=1.4.3 in /usr/local/lib/python3.12/dist-packages (from huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (1.5.0)
    Requirement already satisfied: packaging>=20.9 in /usr/local/lib/python3.12/dist-packages (from huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (26.2)
    Requirement already satisfied: pyyaml>=5.1 in /usr/local/lib/python3.12/dist-packages (from huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (6.0.3)
    Requirement already satisfied: tqdm>=4.42.1 in /usr/local/lib/python3.12/dist-packages (from huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (4.67.3)
    Requirement already satisfied: typer>=0.20.0 in /usr/local/lib/python3.12/dist-packages (from huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (0.25.1)
    Requirement already satisfied: click>=8.2.1 in /usr/local/lib/python3.12/dist-packages (from typer>=0.20.0->huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (8.4.0)
    Requirement already satisfied: shellingham>=1.3.0 in /usr/local/lib/python3.12/dist-packages (from typer>=0.20.0->huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (1.5.4)
    Requirement already satisfied: rich>=13.8.0 in /usr/local/lib/python3.12/dist-packages (from typer>=0.20.0->huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (13.9.4)
    Requirement already satisfied: annotated-doc>=0.0.2 in /usr/local/lib/python3.12/dist-packages (from typer>=0.20.0->huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (0.0.4)
    Requirement already satisfied: markdown-it-py>=2.2.0 in /usr/local/lib/python3.12/dist-packages (from rich>=13.8.0->typer>=0.20.0->huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (4.2.0)
    Requirement already satisfied: pygments<3.0.0,>=2.13.0 in /usr/local/lib/python3.12/dist-packages (from rich>=13.8.0->typer>=0.20.0->huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (2.20.0)
    Requirement already satisfied: mdurl~=0.1 in /usr/local/lib/python3.12/dist-packages (from markdown-it-py>=2.2.0->rich>=13.8.0->typer>=0.20.0->huggingface-hub<2.0,>=0.16.4->tokenizers<1,>=0.15->cohere) (0.1.2)
    Downloading cohere-7.0.2-py3-none-any.whl (351 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m351.9/351.9 kB[0m [31m9.4 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading fastavro-1.12.2-cp312-cp312-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl (3.4 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m3.4/3.4 MB[0m [31m52.1 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading types_requests-2.33.0.20260518-py3-none-any.whl (21 kB)
    Installing collected packages: types-requests, fastavro, cohere
    Successfully installed cohere-7.0.2 fastavro-1.12.2 types-requests-2.33.0.20260518
    


```python
co = cohere.Client(COHERE_API_KEY)
response = co.chat(
    chat_history =[
        {"role": "USER", "message": "What is a reconcialiation matching strategy"},
        {"role": "CHATBOT", "message": "How can Microsoft Copilot leverage reconciliation reporting"}
    ],
    message= "Develop a VBA code to complete matches in bank reconciliation, /n Develop a python code to complete matches in bank reconciliation"
)
print(response.text)
```

    Below are examples of **VBA (Excel)** and **Python** code to automate bank reconciliation matching. These scripts assume you have two datasets: one from your internal records and one from the bank statement. The goal is to match transactions based on criteria like amount, date, and description.
    
    ---
    
    ### **VBA Code for Bank Reconciliation Matching**
    This VBA script compares two tables in Excel and marks matches.
    
    ```vba
    Sub BankReconciliationMatching()
        Dim ws As Worksheet
        Dim internalTable As Range, bankTable As Range
        Dim internalLastRow As Long, bankLastRow As Long
        Dim i As Long, j As Long
        Dim matchFound As Boolean
        
        ' Set the worksheet
        Set ws = ThisWorkbook.Sheets("Sheet1")
        
        ' Define the internal records table (e.g., A2:C100)
        Set internalTable = ws.Range("A2:C100")
        internalLastRow = ws.Cells(ws.Rows.Count, "A").End(xlUp).Row
        
        ' Define the bank statement table (e.g., E2:G100)
        Set bankTable = ws.Range("E2:G100")
        bankLastRow = ws.Cells(ws.Rows.Count, "E").End(xlUp).Row
        
        ' Loop through internal records
        For i = 2 To internalLastRow
            matchFound = False
            ' Loop through bank statement records
            For j = 2 To bankLastRow
                ' Check if amount and date match (adjust criteria as needed)
                If ws.Cells(i, "B").Value = ws.Cells(j, "F").Value And _
                   ws.Cells(i, "C").Value = ws.Cells(j, "G").Value Then
                    ' Mark as matched in both tables
                    ws.Cells(i, "D").Value = "Matched"
                    ws.Cells(j, "H").Value = "Matched"
                    matchFound = True
                    Exit For ' Move to the next internal record
                End If
            Next j
            ' If no match found, mark as unmatched
            If Not matchFound Then
                ws.Cells(i, "D").Value = "Unmatched"
            End If
        Next i
        
        MsgBox "Reconciliation completed!"
    End Sub
    ```
    
    **Assumptions:**
    - Internal records are in columns **A:C** (e.g., A=ID, B=Amount, C=Date).
    - Bank statement records are in columns **E:G** (e.g., E=ID, F=Amount, G=Date).
    - Results are marked in columns **D** (Internal) and **H** (Bank).
    
    ---
    
    ### **Python Code for Bank Reconciliation Matching**
    This Python script uses Pandas to compare two datasets and identify matches.
    
    ```python
    import pandas as pd
    
    # Sample data (replace with your actual data)
    internal_records = {
        'ID': [1, 2, 3],
        'Amount': [100, 200, 300],
        'Date': ['2023-10-01', '2023-10-02', '2023-10-03']
    }
    
    bank_statement = {
        'ID': [2, 3, 4],
        'Amount': [200, 300, 400],
        'Date': ['2023-10-02', '2023-10-03', '2023-10-04']
    }
    
    # Convert to DataFrames
    internal_df = pd.DataFrame(internal_records)
    bank_df = pd.DataFrame(bank_statement)
    
    # Function to match transactions
    def reconcile(internal_df, bank_df):
        internal_df['Status'] = 'Unmatched'
        bank_df['Status'] = 'Unmatched'
        
        for index_i, row_i in internal_df.iterrows():
            for index_b, row_b in bank_df.iterrows():
                if row_i['Amount'] == row_b['Amount'] and row_i['Date'] == row_b['Date']:
                    internal_df.at[index_i, 'Status'] = 'Matched'
                    bank_df.at[index_b, 'Status'] = 'Matched'
                    break  # Move to the next internal record
        
        return internal_df, bank_df
    
    # Perform reconciliation
    internal_matched, bank_matched = reconcile(internal_df, bank_df)
    
    # Display results
    print("Internal Records:")
    print(internal_matched)
    print("\nBank Statement:")
    print(bank_matched)
    ```
    
    **Output Example:**
    ```
    Internal Records:
       ID  Amount        Date    Status
    0   1     100  2023-10-01  Unmatched
    1   2     200  2023-10-02    Matched
    2   3     300  2023-10-03    Matched
    
    Bank Statement:
       ID  Amount        Date    Status
    0   2     200  2023-10-02    Matched
    1   3     300  2023-10-03    Matched
    2   4     400  2023-10-04  Unmatched
    ```
    
    ---
    
    ### **Key Considerations for Both Scripts:**
    1. **Matching Criteria:** Adjust the criteria (e.g., amount, date, description) based on your needs.
    2. **Fuzzy Matching:** For partial matches (e.g., descriptions), use fuzzy matching libraries like `fuzzywuzzy` in Python.
    3. **Performance:** For large datasets, optimize the code (e.g., use vectorized operations in Pandas).
    4. **Error Handling:** Add checks for missing data or invalid formats.
    
    Let me know if you need further customization!
    
