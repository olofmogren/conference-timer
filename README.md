# Conference Program Timer

A full-screen HTML-based timer designed to display the current speaker/event and a countdown to the next schedule change (or Q&A session) for a conference or workshop. It includes a visual progress bar for the current minute and allows for live schedule delays.

## Features

-   Full-screen display with black background and white text.
-   Top bar (10% height) shows the current speaker/event.
    -   During breaks, it also shows the next event and its start time.
-   Main area (90% height) shows a large countdown number (minutes remaining).
-   **Breaks**: A 5-minute Q&A period is automatically initiated before the scheduled end of talks.
    -   During the main talk, the timer counts down to the start of Q&A.
    -   During Q&A, the top bar shows "Questions", and the timer counts down the remaining 5 minutes in red.
-   **Minute Progress Bar**: A horizontal bar under the timer number visually represents the current minute.
    -   The colored (filled) part is right-aligned and shrinks from left to right as the minute progresses.
    -   The bar's color matches the timer number (white or red during Q&A).
-   **Dynamic Schedule Delay**: Press the 'd' key to open a prompt and enter a delay in minutes (positive to delay, negative to advance). The entire schedule adjusts accordingly. A small note in the bottom right indicates the current delay. The delay is reset at the next break.
-   **Schedule Embedded in HTML**: The program schedule is embedded as CSV-formatted text directly within the `timer.html` file for easy editing and portability.

## Files

-   `timer.html`: The main HTML file containing the display logic, JavaScript, and embedded schedule data.

## Setup and Usage

1.  **Edit Schedule**:
    -   Open `timer.html` with a text editor.
    -   Locate the `<script type="text/csv-data" id="scheduleDataCsv">` tag (usually near the top, after the `<style>` block).
    -   The content inside this tag is the schedule in CSV format.
    -   The first line **must** be the headers: `startTime,endTime,speaker`.
    -   Each subsequent line represents a schedule slot.
    -   `startTime` and `endTime` should be in **HH:MM** (24-hour) format.
    -   `speaker` is the text to be displayed for that slot.
    -   *See Embedded Schedule Format section below for an example.*
    -   Save the `timer.html` file after making changes.
2.  **Open Timer**: Open `timer.html` in a web browser (e.g., Chrome, Firefox, Edge). It should work directly from your local file system.
3.  **Live Delay**: During the event, if the schedule needs to be adjusted:
    -   Press the 'd' key on the keyboard.
    -   A dialog box will appear. Enter the number of minutes to delay the schedule (e.g., `10` to delay by 10 minutes, `-5` to advance by 5 minutes).
    -   Press Enter or click OK. The timer and all future events will adjust.

## Embedded Schedule Format (within `timer.html`)

Inside `index.html`, find the section:
```html
<!-- Embedded Schedule Data -->
<script type="text/csv-data" id="scheduleDataCsv">
startTime,endTime,speaker
08:00,09:00,Coffee / Find your seat
09:00,09:15,Olof Mogren
09:15,10:00,Keynote 1: Oisin Mac Aodha
... (more entries)
</script>
<!-- End Embedded Schedule Data -->
