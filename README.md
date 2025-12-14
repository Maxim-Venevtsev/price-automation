# price-automation

Automated multi-step ETL pipeline for processing supplier price lists.
It performs structured data cleaning, normalization, validation, comparison with a base catalog, and generates a fully formatted dealer-ready price file.
The system includes Excel automation, conditional formatting, logging, and batch execution (EXE build).

📌 Features

Automatic ingestion of incoming supplier files (XLS, XLSX, CSV)

Multi-stage cleaning & normalization pipeline

Price group validation against a base catalog

Detection of new and missing SKUs

Automatic price substitution rules

Formatted dealer price output (Output_price_yyyy_mm_dd.xlsx)

Optional Outlook file fetching (future extension)

EXE build for one-click execution

📂 Project Structure
price-automation/
│
├── scripts/
│   ├── process_prices_1.py      # Load & extract raw input
│   ├── process_prices_2.py      # Restructure columns
│   ├── process_prices_3.py      # Remove empty groups
│   ├── process_prices_4.py      # Deep text cleaning & normalization
│   ├── process_prices_5.py      # Compare with base price catalog
│   ├── process_prices_6.py      # Create final formatted output
│   └── process_all.py           # Super-script orchestrating all steps
│
├── clean/                       # Intermediate cleaned files
├── base/                        # Base catalog
├── incoming/                    # Supplier raw files
├── output/                      # Final dealer price files
└── logs/                        # Run logs

🧩 ETL Pipeline Overview (Mermaid Diagram)
flowchart TD

    A[Incoming Supplier File<br>(XLS / XLSX / CSV)] --> B[STEP 1:<br>Load & extract data]
    B --> C[STEP 2:<br>Restructure column schema]
    C --> D[STEP 3:<br>Remove empty or invalid groups]
    D --> E[STEP 4:<br>Text cleanup & normalization]
    E --> F[STEP 5:<br>Compare with base catalog<br>Detect new & known SKUs]
    F --> G[STEP 6:<br>Generate formatted dealer file]

    G --> H[Output_price_yyyy_mm_dd.xlsx]

    subgraph CLEANING PIPELINE
        B --> C --> D --> E
    end

    subgraph FINAL OUTPUT
        F --> G --> H
    end

📄 Final Output Example

The system produces a clean, formatted Excel file, including:

Renamed & ordered columns

Numeric formatting

Conditional formatting for new SKUs

Branded header layout

Dealer-ready structure

Example output file name:

Output_price_2025_01_10.xlsx

🚀 Running the Pipeline
python scripts/process_all.py


Or run the compiled EXE:

process_all.exe

🔧 Technology Stack

Python 3.11

Pandas

OpenPyXL

PyInstaller (for EXE build)

Outlook COM Automation (optional extension)

📬 Contact

If you find the project useful or have questions — feel free to reach out via GitHub Issues.
