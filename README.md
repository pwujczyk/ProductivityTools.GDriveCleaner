# ProductivityTools.GDriveCleaner

Google Apps Script that moves Google Drive files whose names start with `ToTrash` to the trash.

## How It Works

- **Server-side search (`DriveApp.searchFiles`)**: Queries Google Drive directly for non-trashed files owned by the current user with `ToTrash` in the title (`trashed = false and "me" in owners and title contains "ToTrash"`), avoiding iterating over the entire Drive.
- **Prefix & ownership check**: Confirms each file's name starts with `ToTrash` (`name.startsWith("ToTrash")`) and is owned by the active user before moving it to trash (`file.setTrashed(true)`).
- **Timeout protection**: Stops execution after 5 minutes (`maxExecutionTimeMs = 5 * 60 * 1000`) or 10,000 processed files so it exits cleanly before hitting Google Apps Script's 6-minute execution limit (`Exceeded maximum execution time`).

## Usage

1. Open [Google Apps Script](https://script.google.com/) and create a new project.
2. Copy the code from `Script.txt` into the script editor.
3. Run `myFunction` manually or configure a time-driven trigger to run it periodically.

