# FAQ

Here we'll answer some frequently asked questions about ecs-utdevents. If you can't find the answer to your question here or you'd like to report a bug with the website then email us at: [utdecsevents@gmail.com](mailto:utdecsevents@gmail.com)

Testing live change.

## As a user...
**Q: Whose events can I see?**

A: You are able to see all events that our partner organizations have added! This may be a lot of events so you can also filter through them by specific organization, tags, and start and end time. 

**Q: Can I add events?**

A: No. Only partner organizations who have been approved by us can add events to the website. This is to ensure that you don't ever see inappropriate, spam, or fake events.

**Q: How can I save an event to my calendar?**

A: Once you select an event from the calendar it should either show up on the left hand side of the window or pop up from below. If you look at the bottom right corner of this event information you'll see a button with a calendar icon. Clicking on this button will download a .ics file with all the event information in it. You can then drag and drop this file into iCal and Outlook or you can import it into your Google Calendar. Unfortunately this feature does not currently work on mobile devices that don't support internet file downloads.

**Q: Can I save multiple events?**

A: Unfortunately this feature is not currently available. If you don't already see a feature you want, feel free to add it [here](https://github.com/ecs-utd-events/ecs-utd-events/issues).

**Q: Can I report a bug?**

A: Yes of course! We always appreciate feedback to help improve this project. Please create an issue on our [github project](https://github.com/ecs-utd-events/ecs-utd-events/issues) and someone will try to look into it as soon as possible.

**Q: Can I contribute to this project?**

A: Yup! All of our code is open-sourced and we are always open to new pull requests. Take a look at the [documentation for Developers](./frontend.md) for more info on how to get started.

## As an organization...
**Q: How do I sign up to use this platform?**

You can sign up [here](https://forms.gle/jjV72W34txZLvZuw7)! We'll then begin the process of verifying that you are an in fact a UTD student organization that is affiliated with ECS. If you haven't received a reply in over a week and believe that you should have been approved you can send us a reminder at [utdecsevents@gmail.com](mailto:utdecsevents@gmail.com).

**Q: Who can see my events and where?**

Anyone who knows about ecs-utdevents will be able to see your events. They can view them on the calendar on the home page or on your organization's profile page (these are found at /org/org-slug, i.e. /org/society-of-women-engineers). 

**Q: Who can edit my event?**

All collaborators listed on an event are able to edit it.

**Q: Can I add an external collaborator to my event?**

Currently we do no support "Other" or external collaborators. If there is another ECS student organization working with you on an event then we recommend they also join our platform!

**Q: How can I use my data on the website for other purposes?**

You can access our Public API to retrieve all your event data! You could use this in any way you wish; you could create a discord bot that notifies your server about upcoming events or display your events directly on your organization's website or really anything! Check out our [API documentation](./api_documentation.md) for more info.

**Q: Why doesn't my profile photo show up?**

When adding a new profile photo URL you may need to refresh the page to see updates. If you are instead seeing an empty box then this probably means that the URL you've given does not lead directly to the image. Make sure when you put the URL into your browser that you navigate to just the image not a webpage with the image on it. These image URLs should end in .jpg/.jpeg/.png or another image format. You can usually find an image URLs by right-clicking on an image and selecting **"Copy Image Address"**
