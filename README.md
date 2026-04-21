# ELUNA DD+ 2026

## Patron Checker: Alma User Management Automation

This repository demonstrates how to automate Alma user management tasks using code and APIs. The scripts here are designed for real-world library workflows, but also serve as examples for learning and adapting to your own needs.

--------------------------------------------------------------------------

### What You Can Do With These Scripts 

* <b>Check for missing expiration dates</b> Identify users who don’t have an expiration date set.

* <b>Add expiration dates in bulk</b> Automatically assign expiration dates to users, filtered by patron type (e.g., undergraduates, staff, etc.).

* <b>Bulk deactivate users</b> Set users listed in a file (e.g., ```deactivate.txt```) to "inactive" in Alma. 

* <b>Create Alma sets for inactive users</b> Use exported lists to create Alma sets for further processing or reporting.

* <b>Verify purge eligibility</b> Check that all users in a group (e.g., "PurgePending") are past a chosen expiration date. 

* <b>Purge users in Alma</b> Use Alma's built-in tools to remove users after verification. 

-------------------------------------------------------------------------

### Demo Workflow 

1. <b>Check if expiration date is blank</b> (Python: `expiration-checker.py`)

2. <b>Add expiration date if blank, by patron type

    * Retrieve list of patron types
    * Select patron type
    * Add expiration date to that patron type (Python: `add_purge_dates.py`)

3. <b>Export users by expiration date</b>
    * If user has expiration date before/after a manually inputted date, print their Primary ID to a txt file (Python/Go: `expiration-checker.py` or expiration-checker.go`)

4. <b>Bulk deactivate users</b>
    * Render everyone from `deactivate.txt` as "inactive" in Alma (Python: `deactivate-users.py`)

5. <b>Create Alma set for inactive users</b>
    * Use exported lists to create sets in Alma (manual step)

6. <b>Verify purge eligibility</b> 
    * Use `verify_purge_pending.py` to check that everyone in the group is past the chosen expiration date (Python: `verify_purge_pending.py`)

7. <b>Purge users in Alma</b>
    * Use Alma's built-in purge tools (manual step) 

--------------------------------------------------------------------------

### Setup

1. <b>Install dependencies</b> (for Python scripts): 

2. <b>Configure API credentials:</b>

    * Add your Alma API key and base URL to `.env` (production) and/or `.env.sandbox` (sandbox/testing)

3. <b>Run scripts:</b>

    * Python: `python3 script_name.py` (or python script_name.py)
    * Go: `go run script_name.go`

-------------------------------------------------------------------------

### Notes

* All scripts are designing to be safe for testing in Alma Sandbox before running in production

* Output files are timestamped for easy tracking and auditing

* See comments in each script for detailed explanations of each step 

* Feel free to reach out to me at brandon.katzir@uri.edu 
