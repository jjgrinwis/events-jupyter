# Events Jupyter Quickstart

This project contains a Jupyter notebook for querying Akamai Event Viewer API data.

## Requirements

- Git
- Python 3.10+
- uv
- Akamai API credentials configured in ~/.edgerc

Install uv if needed:

- macOS: brew install uv
- Windows (PowerShell): powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
- Linux/macOS (alternative): curl -LsSf https://astral.sh/uv/install.sh | sh

## Clone the project

1. Clone the repository:
   git clone <your-repo-url>
2. Enter the project folder:
   cd events-jupyter

## Set up with uv

1. Create the environment and install dependencies:
   uv sync

2. (Optional) Set the EdgeGrid section if not using default:
   export AKAMAI_EDGEGRID_SECTION="gss"

3. (Optional) Set account switch key when needed:
   export AKAMAI_ACCOUNT_SWITCH_KEY="1-2345:A-BCDE"

## Run the notebook

Start Jupyter Lab through uv:

uv run jupyter lab event-vieuwer.ipynb

Then run the notebook cells from top to bottom.

## What the notebook does

- Creates an authenticated EdgeGrid session
- Fetches event types for:
  - All Logins
- Fetches events with pagination support
- Handles API rate limiting by waiting between paginated requests
- Prints a total count and only the first 2 events for debugging output

## Troubleshooting

- 400 Bad Request:
  - Confirm timestamp format and query params in the event request cell.
  - Verify your credentials and API permissions for Event Viewer.

- 429 Too Many Requests:
  - The notebook already delays between pages.
  - Increase the delay in the events cell if needed.

- Authentication issues:
  - Ensure ~/.edgerc exists and includes the section set in AKAMAI_EDGEGRID_SECTION.
