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
5. Select **Create schedule**. The app checks about once an hour. The first issue is created on the first check after the time you chose, and the list then shows the last run or the error.

You can pause or remove a schedule at any time from the same page. A schedule belongs to the whole Jira site, so every schedule is visible to people who can open the app.

## Worked example

On 19 November 2026 a private Jira site used a development install, which is not a Marketplace install. The schedule was:

- Project `SHOP`, issue type Task (`10001`)
- Summary: `Weekly storefront stock check (QA R70)`
- Description: `QA run for Recurring Work: verify the scheduled issue is created once and the next run is scheduled.`
- Repeat: every day
- First run: 19 November 2026, 18:00, America/Sao_Paulo

The hourly check at 18:55 America/Sao_Paulo created issue `SHOP-8` at 18:55:49, reported by Recurring Work for Jira, with the label `recurring-mwo05iuczanla02h-mwo1ag00`. That check did not save the schedule row. After a fix to that save, the next check found the same label, left `SHOP-8` as the only matching issue, and saved `Last run: Already created: SHOP-8`. The next run shown was 20 November 2026, 18:00. The schedule was then paused so the private site would not open another task the next day.

The Marketplace listing is not published, so there is no public install link yet.

## Finding the issue type ID

Run `forge`-free: open `https://your-site.atlassian.net/rest/api/3/issue/createmeta?projectKeys=OPS&expand=projects.issuetypes` in a browser where you are signed in, and read the `id` of the issue type you want. The Jira UI also shows it in the issue type settings of the project.

## Support

Open a ticket at <https://portal.designmastersolutions.com/submitticket.php> and include your Jira site name and the schedule's summary.

## Privacy and terms

- Privacy: <https://www.designmastersolutions.com/privacy.html#atlassian-apps>
- Terms: <https://www.designmastersolutions.com/terms.html>

## Who makes it

Design Master Solutions builds Jira and Confluence apps that stay inside Atlassian: <https://www.designmastersolutions.com>.
