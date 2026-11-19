# Recurring Work for Jira

User guide and support for **Recurring Work for Jira**, an Atlassian Forge app that creates the same Jira work item on a daily, weekday, weekly, or monthly schedule.

## What it does

- Creates a new Jira issue from a schedule you set: project, issue type, summary, and description.
- Repeats daily, Monday to Friday, weekly, or monthly.
- Keeps the local run time you chose, including across daylight-saving changes, and goes back to the 29th, 30th, or 31st after a shorter month.
- Looks for the issue it would create before creating it, so a retry after a Jira error does not duplicate work.
- Retries a failed run on later hourly checks, up to five times, then pauses the schedule and shows the last error.
- Runs entirely on Atlassian's Forge platform. We have no servers for it.

## Set up a schedule

1. In Jira, open **Apps > Recurring Work**.
2. Fill in the project key (for example `OPS`) and the issue type ID of the project (for example the ID of *Task*).
3. Write the issue summary and, if you want, the description that every run will copy.
4. Pick the first run date and time, and how often it repeats.
5. Select **Create schedule**. The first issue is created at the selected time, and the list shows the last run and any error.

You can pause or remove a schedule at any time from the same page. A schedule belongs to the whole Jira site, so every schedule is visible to people who can open the app.

## Finding the issue type ID

Run `forge`-free: open `https://your-site.atlassian.net/rest/api/3/issue/createmeta?projectKeys=OPS&expand=projects.issuetypes` in a browser where you are signed in, and read the `id` of the issue type you want. The Jira UI also shows it in the issue type settings of the project.

## Support

Open a ticket at <https://portal.designmastersolutions.com/submitticket.php> and include your Jira site name and the schedule's summary.

## Privacy and terms

- Privacy: <https://www.designmastersolutions.com/privacy.html#atlassian-apps>
- Terms: <https://www.designmastersolutions.com/terms.html>

## Who makes it

Design Master Solutions builds Jira and Confluence apps that stay inside Atlassian: <https://www.designmastersolutions.com>.
