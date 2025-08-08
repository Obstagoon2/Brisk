# FRC Team 1912 Website

A modern, responsive website for FRC Team 1912 built with HTML, CSS, and JavaScript.

## Features

- Modern and responsive design
- Google Calendar integration to display upcoming events
- Smooth scrolling animations
- Interactive navigation
- Parallax effects
- Mobile-friendly layout
- Section-based content organization

## Project Structure

```
1912website/
├── index.html          # Main HTML file
├── about.html          # About page
├── outreach.html       # Outreach page with Google Calendar
├── ...
├── css/
│   ├── style.css      # Main styles
│   └── ...
├── js/
│   ├── main.js        # Main JavaScript functionality
│   └── calendar.js    # Google Calendar integration
├── assets/             # Image and video assets
└── README.md         # Project documentation
```

## Managing the Google Calendar

The website displays events from a Google Calendar on the `outreach.html` page. The integration is managed by `js/calendar.js`.

### How to Change the Calendar

To change the calendar, you need to update two values in `js/calendar.js`:

1.  `calendarId`: The ID of the Google Calendar to display.
2.  `apiKey`: Your Google Cloud API key.

```javascript
// js/calendar.js

const calendarId = 'YOUR_CALENDAR_ID@group.calendar.google.com';
const apiKey = 'YOUR_GOOGLE_API_KEY';
```

### Getting a Google Calendar ID

1.  Open [Google Calendar](https://calendar.google.com).
2.  In the left sidebar, find the calendar you want to display.
3.  Hover over the calendar, click the three vertical dots, and select "Settings and sharing".
4.  Under the "Integrate calendar" section, you will find the **Calendar ID**. Copy this value.

### Getting a Google API Key

1.  Go to the [Google Cloud Console](https://console.cloud.google.com/).
2.  Create a new project (or select an existing one).
3.  Enable the **Google Calendar API** for your project.
    - Go to "APIs & Services" > "Enabled APIs & services".
    - Click "+ ENABLE APIS AND SERVICES".
    - Search for "Google Calendar API" and enable it.
4.  Create an API key.
    - Go to "APIs & Services" > "Credentials".
    - Click "+ CREATE CREDENTIALS" and select "API key".
    - Copy the generated API key.
5.  **Important**: It is highly recommended to restrict your API key to prevent unauthorized use. You can restrict it to your website's domain (HTTP referrers).

### Making Your Calendar Public

For the website to be able to read calendar events, the Google Calendar must be public.

1.  In your Google Calendar's "Settings and sharing", go to the "Access permissions for events" section.
2.  Check the box for "Make available to public".
3.  Select "See only free/busy (hide details)" or "See all event details" depending on what you want to show.

## Diagnosing Calendar Issues

If the calendar events are not showing up on the outreach page, here are some things to check:

-   **"Failed to load events" message**: This is the most common error. It usually means there is a problem with your `calendarId` or `apiKey` in `js/calendar.js`.
-   **Check the Browser Console**: Open your browser's developer tools (usually by pressing F12) and check the Console tab for more detailed error messages from the Google Calendar API.
-   **Is the Calendar Public?**: Double-check that your Google Calendar is set to public.
-   **API Key Restrictions**: If you have restricted your API key, make sure the restrictions are configured correctly. For example, if you restricted it to a specific domain, it might not work when you are testing the website locally.

## Customizing the Calendar Display

You can change how many events are loaded at a time by modifying the `EVENTS_PER_BATCH` constant in `js/calendar.js`.

```javascript
// js/calendar.js

const EVENTS_PER_BATCH = 6; // Change this number to show more or fewer events per batch
```

## License

This project is open source and available under the MIT License.
