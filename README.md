# Debate Tool

A real-time web platform for moderating and facilitating structured debates involving a **Spotlight Speaker**, **Challengers**, and a **Moderator**. Built with [Firebase Realtime Database](https://firebase.google.com/) for instant synchronization.

---

## Features

- **Role-based login**: Users join as **Moderator**, **Spotlight Speaker**, or **Challenger**.
- **Topic management**: Spotlight Speaker sets the current debate topic.
- **Challenger queue**: Challengers indicate readiness by clicking "Challenge Now." Only one active challenger at a time, selected manually by the Moderator.
- **Voting system**: Non-active Challengers can vote to "change" the current Challenger; voting status is visible to the Moderator in real-time.
- **Timer**: Moderator starts and resets a round timer.
- **Live status board**: Moderator’s dashboard displays the current topic, timer, and all Challenger voting statuses (color-coded).
- **Session reset**: Moderator can reset the debate, clearing all data.

---

## How It Works

### 1. Joining the Debate

- On loading the app, users enter their name and choose a role:
  - **Moderator**: Oversees the session, manages timer, selects current Challenger, and resets debate.
  - **Spotlight Speaker**: Proposes topics for debate.
  - **Challenger**: Can become the current Challenger and participate in voting.

### 2. Debate Flow

1. **Spotlight Speaker** enters a topic, which is displayed to all.
2. **Challengers** can click **"Challenge Now"** (only available if there is no current Challenger). The Moderator can manually assign any Challenger as the current Challenger.
3. **Moderator** starts the timer for the round.
4. **Non-active Challengers** can vote for a change by clicking **"Vote for Change"**. They can also **cancel** their vote.
   - Voting status is shown as **green** (not voted) or **red** (voted) circles with each Challenger’s name on the Moderator’s dashboard.
   - If more than half of Challengers vote for change, Moderator may manually switch the current Challenger.
5. When the timer ends, the process restarts with a new topic.

---

## Technology Stack

- **Frontend**: Vanilla JavaScript, HTML, CSS
- **Realtime Database**: [Firebase Realtime Database](https://firebase.google.com/docs/database)
- **Authentication**: Firebase Anonymous Auth

---

## Quick Start

1. **Clone the repository:**
   ```bash
   git clone https://github.com/EricFong-dev/debate-tool.git
   cd debate-tool
   ```

2. **Setup Firebase:**
   - Update `firebaseConfig` in the HTML/JS source with your own Firebase project credentials (or use the provided config if you're a collaborator).

3. **Run locally:**
   - Open `index.html` in your browser.

   > You can also deploy using [Firebase Hosting](https://firebase.google.com/docs/hosting).

---

## Project Structure

```
index.html         # Main application file
README.md          # Project documentation
```

- All logic is handled in a single HTML file for simplicity.
- Uses Firebase modules via CDN.

---

## Roles and Permissions

- **Moderator**
  - Sees all Challengers and their voting statuses.
  - Selects current Challenger.
  - Starts/ends timer.
  - Resets the debate session.

- **Spotlight Speaker**
  - Sets the discussion topic.

- **Challenger**
  - Can become the current Challenger (when no one else is).
  - Votes for or cancels a vote to change the current Challenger.

---

## Data Structure (Firebase)

```
debate/
  users/
    {uid_sessionId}
  moderator/
    {uid_sessionId}
  spotlight/
    {uid_sessionId}
  challengers/
    {uid_sessionId}
  votes/
    {uid_sessionId}: true|false
  currentChallenger/
    { name, uid, sessionId }
  topic/
  timer/
    { start, duration, timestamp }
```

---

## License

This project is licensed under the MIT License.

---

## Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

---

## Acknowledgments

- [Firebase](https://firebase.google.com/)
- [Google Fonts](https://fonts.google.com/)
- [Cursor](https://www.cursor.com/)
```
