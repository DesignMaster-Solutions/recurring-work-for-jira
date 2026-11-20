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
2. Type the project key (for example `OPS`). The issue type list fills with the types that project can create. Pick one by name. Subtasks stay off the list, because a schedule has no parent issue.
3. Write the issue summary and, if you want, the description that every run will copy.
4. Pick the first run date and time, and how often it repeats.
5. Select **Create schedule**. The app checks about once an hour. The first issue is created on the first check after the time you chose, and the list then shows the last run or the error.

You can pause or remove a schedule at any time from the same page. A schedule belongs to the whole Jira site, so every schedule is visible to people who can open the app.

## What Create schedule tells you

Production and development, deployed 20 November 2026, answer Create schedule with "Schedule created." and this note, which also sits under the time field: "Jira checks about once an hour. The issue is created on the first check after the time you chose, not at that exact minute."

A weekday schedule refuses a Saturday or Sunday first run and keeps Create schedule disabled until the first date is Monday through Friday. The message is: "Weekday schedules start on Monday through Friday. Choose a weekday for the first run."

On 20 November 2026 a development install, which is not a Marketplace install, showed that message for a first run of 21 November 2026 (a Saturday) and left Create schedule disabled. The same screen showed the hourly note.

## What the list shows

Under each schedule the line uses the schedule's own time zone. For the worked example's next check it reads:

`Every day · Earliest check: 20 Nov 2026, 18:00 (America/Sao_Paulo)`

That time is the earliest moment the hourly check may create the issue. On 20 November 2026 the paused SHOP-8 row on the development install showed that line, with Last run "Already created: SHOP-8" and status Paused. That check did not resume, delete, or create another schedule.

The crop below is that screen without the Jira sidebar or the account bar. It ends on the earliest-check line because the window cut off the Last run line.

![SHOP lists Bug, Epic, Story and Task. The paused schedule shows the earliest check.](highlight-types-and-earliest-check.jpg)

## When the last error does not name a field

The schedule shows the last error after a failed check. If that text does not name the field Jira rejected, open the project and start one issue of the same type. The create screen lists required fields this app does not ask for, such as priority. Make that field optional, or give it a default, then resume the schedule. A subtask fails for a different reason: the schedule has no parent issue, so choose a standard type instead.

## Worked example

On 19 November 2026 a private Jira site used a development install, which is not a Marketplace install. The schedule was:

- Project `SHOP`, issue type Task (`10001`)
- Summary: `Weekly storefront stock check (QA R70)`
- Description: `QA run for Recurring Work: verify the scheduled issue is created once and the next run is scheduled.`
- Repeat: every day
- First run: 19 November 2026, 18:00, America/Sao_Paulo

The hourly check at 18:55 America/Sao_Paulo created issue `SHOP-8` at 18:55:49, reported by Recurring Work for Jira, with the label `recurring-mwo05iuczanla02h-mwo1ag00`. That check did not save the schedule row. After a fix to that save, the next check found the same label, left `SHOP-8` as the only matching issue, and saved `Last run: Already created: SHOP-8`. The next run shown was 20 November 2026, 18:00. The schedule was then paused so the private site would not open another task the next day.

The Marketplace listing is not published, so there is no public install link yet.

## Choosing the issue type

The form lists type names. You do not type a numeric ID. The line under the list says: "The list is the types this project can create. Subtasks stay off the list because a schedule has no parent issue." The open list for project SHOP is in the crop under [What the list shows](#what-the-list-shows).

On 20 November 2026, project `SHOP` on the development install offered Bug, Epic, Story, and Task. No subtask. A project key Jira does not know stays on the form as Jira's own sentence. Typing `SHOPSHOP` showed: "Jira 404 reading issue types for SHOPSHOP. No project could be found with id or key 'SHOPSHOP'." Replacing it with `SHOP` loaded the type list.

To read the same IDs outside the app, open this URL while you are signed in to that Jira site, and replace `OPS` with the project key:

`https://your-site.atlassian.net/rest/api/3/issue/createmeta?projectKeys=OPS&expand=projects.issuetypes`

Read `projects[].issuetypes[]`. Copy the `id` whose `subtask` is false. The project settings page for issue types shows the same ID.

If the body is `{"expand":"projects","projects":[]}`, that browser is not signed in to the site. On 19 November 2026, `https://dms-release-gate.atlassian.net/rest/api/3/issue/createmeta?projectKeys=SHOP&expand=projects.issuetypes` returned HTTP 200 with that empty list and no session. A signed-in page lists the types under `projects`.

## Support

Open a ticket at <https://portal.designmastersolutions.com/submitticket.php> and include your Jira site name and the schedule's summary.

## Privacy and terms

- Privacy: <https://www.designmastersolutions.com/privacy.html#atlassian-apps>
- Terms: <https://www.designmastersolutions.com/terms.html>

## Who makes it

Design Master Solutions builds Jira and Confluence apps that stay inside Atlassian: <https://www.designmastersolutions.com>.
