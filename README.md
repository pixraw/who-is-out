# Who is Out

No more pestering your coworkers about an upcoming vacation or forgetting to tell people about a doctor appointment because you "added it to your calendar" and forgot about it.

This set of Google Apps Scripts automatically creates an aggregated calendar of who and when everyone will be out of office, then emails your team a daily digest summarizing out-of-office time for the next few weeks.

![Screenshot](http://dropshare-superstrong.s3.amazonaws.com/XfBD5oLxNGgcJR/Screen-Shot-2016-12-16-at-9.55.43-PM.png)

## Usage

Just invite the new `out@<yourdomain>` user to your event and it will show up in the digest. The title of the event will be replaced by a generic description based on keywords in the title, such as `working remote`, `sick/doctor`, `event/conference/meeting`, etc. -- whatever you want.

## Installation

### As a G Suite admin
- Go to the [developer console](https://console.developers.google.com) and enable the following APIs: **Admin SDK**, **Google Calendar API**
- Log in to the [admin console](https://admin.google.com) and create a new user, such as `out@<yourdomain>`
- Give the user the following elevated privileges: **User Management Admin**

### As the new user
- Create a second calendar that will be used to aggregate events. e.g., "Who is Out" or Out and Away"
- Create a new Google Sheet (name doesn't matter), then open Tools -> Script editor...
- In your script project, open Resources -> Developers Console Project...
- An overlay will say "This script is currently associated with project:" ... click the link
Enable the following API: **Admin SDK**

Now we can configure the scripts.

- Create `events.gs`, `digest.gs`, and `trigger.gs` and copy/paste the contents
- In `trigger.gs`, replace the calendar and email variables with your own
    - Note: Set the recipient to something you can test with, such as your own email address
- In `trigger.gs`, run `hourly()` and `daily()` manually. This will cause them to prompt you for permission, which you should approve.

### Set to autopilot
- Replace the `recipient` variable in `trigger.gs` with your desired distribution address, such as `everyone@<yourdomain>`
- Create an hourly trigger for `hourly()`
- Create a daily trigger for `daily()`. By default it will run every day except Saturday.

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :)

## History

Inspired by a daily digest we had at Cover in NYC (RIP).

## Credits

The foundation for this project is two old scripts cobbled together:

- events.gs is based on [Google Apps Script Vacation Calendar](https://github.com/sobodda/Google-Apps-Script-Vacation-Calendar) by Stephanie Obodda
- digest.gs is based on [Daily Digest](https://ctrlq.org/code/19961-google-calendar-agenda-email) by [Amit Agarwal](https://github.com/labnol)

## License

[MIT License](https://opensource.org/licenses/MIT)
