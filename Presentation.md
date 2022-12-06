# FairShare
### A household sharing application

---

## What is FairShare?

<small>


- FairShare is an application for facilitating the fair sharing of communal goods.
- Participating members of the household join a group on the application, where they can buy from, or sell to, the communal pot.
- When it is time for a member to leave, or when the users wish to even up the debts, each member's balance can be checked and reset at once; the users will exchange money according to their spending.

</small>

---

## Product backlog

`todo!()`

---

## Task breakdown

<small><small>
<table>
  <thead>
    <tr>
      <th>Title</th>
      <th>Story</th>
      <th>Task</th>
      <th>Owner</th>
      <th>Acceptance Criteria</th>
      <th>Progress</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan=7>Login/Sign Up</td>
      <td rowspan=7>As a user I want to be able to log into the system so that I can see my list of groups.</td>
      <td>Flutter implementation of login page.</td>
      <td rowspan=2>Jacob</td>
      <td>If I enter a username and a password then I should be taken to a home page.</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>Flutter implementation of sign up page.</td>
      <td>If I enter a username, a password, a matching password, an email, and a phone number, then I should be taken to a home page.</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>Database design</td>
      <td rowspan=2>Albany</td>
      <td>Showcase design model with user data, group data, transaction data, and object data.</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>Database user account implementation</td>
      <td>Database demo</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>Back-end user data API Design</td>
      <td rowspan=2>Toby</td>
      <td>API demo?</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>Back-end user data API Implementation</td>
      <td>Code sample?</td>
      <td>In Progress</td>
    </tr>
    <tr>
      <td>API integration between front-end and back-end</td>
      <td>Ben</td>
      <td>Code sample. Test account creation/login. Only go to home page if valid.</td>
      <td>Not Started</td>
    </tr>
    <tr>
      <td>App-wide</td>
      <td>As a user I want an inviting theme that I can instantly recognise.</td>
      <td>Create 2-3 design palettes</td>
      <td>Aiko</td>
      <td>Collect feedback from presentation.</td>
      <td>?</td>
    </tr>
  </tbody>
</table>
</small></small>

---

## User stories

> As a user I want to be able to log into the system so that I can see my list of groups.
- Most tasks were based on this user story.

> As a user I want an inviting theme that I can instantly recognise.
- One task was based on this user story.

---

## Jacob's tasks

<small>

- Task: Flutter implementation of the login page.
    - Acceptance criterion: If I enter a username and a password then I should be taken to a home page.
    - Time expected: 1h
    - Time taken: 30m
- Task: Flutter implementation of the sign up page.
    - Acceptance criterion: If I enter a username, a password, a matching password, an email, and a phone number, then I should be taken to a home page.
    - Time expected: 2h
    - Time taken: 1h

</small>

---

## Albany's tasks

<small>

- Task: Database design
  - Acceptance criterion: Showcase design model with user data, group data, transaction data, and object data.
  - Time expected: 3h
  - Time taken: 2h30m
  - No​tes:
    - The database was first designed, then normalised to 3rd normal form.
    - The following slide contains an image of the database diagram
- Task: Database user account implementation
  - Acceptance criterion: Show example scripts (code sample)

</small>

---

![](https://media.discordapp.net/attachments/1042514869213208706/1049687379327340604/image.png)

---

## Albany's tasks
#### Database implementation of user

```rust
#[derive(Insertable)]
#[diesel(table_name = users)]
pub struct NewUser<'a> {
    pub username: &'a str,
    pub pwd_hash: &'a str,
    pub email: &'a str,
    pub mobile: &'a str,
}
```

```rust
let new_user = NewUser {
    username: "user",
    pwd_hash: "password",
    email: "email",
    mobile: "mobile",
};
diesel::insert_into(users).values(&new_user).execute(conn)
```

---

## Toby's tasks

<small>

- Task: Back-end user data API design
    - Acceptance criterion: Showcase API schema for user-data endpoints.
    - Time expected: 3h
    - Time taken: 2h
    - Schema on next slide
- Task: Back-end user data API implementation
    - Acceptance criterion: Code sample
    - Time expected: 10h
    - Time taken: not yet complete

</small>

---

## Toby's tasks
#### API Schema

<small>

- POST `/login`
    - Takes JSON data, `{"username": string, "password": string}`
    - Returns JSON response; `{"token": string}` on success or `{"error_type": string}` on failure
- POST `/signup`
    - Takes JSON data, `{"username": string, "password": string, "email": string, "mobile": string}`
    - Returns JSON reponse; `{"token": string}` on success or `{"error_type": string}` on failure
- POST `/token`
    - Returns JSON data, `{"token": string}` containing a refreshed token, if the request was correctly authenticated.
- PATCH `/me`
    - Takes JSON data, `{"old_password": string, "new_password": string}`
    - If the request was correctly-authenticated and the old password matched, updates the user's password.

</small>

---

## Toby's tasks
#### API routes code sample

```rust
#[post("/login", format = "json", data = "<data>")]
pub async fn login(
    db: Db,
    data: Json<LoginData>,
) -> JsonResult<LoginResult, GenericError> {
    // code omitted here
}
```

---

## Ben's task

- Task: API integration between front-end and back-end
    - Acceptance criterion: Code sample, demo with integrated API or mock interfaces.
    - Time expected: 3h
    - Time taken: not yet complete
- Task: Backlog refinement
    - Time expected: 3h
    - Time taken: 2h15m

---

## Aiko's task

- Task: Create 2-3 design palettes
    - Acceptance criterion: Collect feedback from this presentation.
    - Time expected: NaNh
    - Time taken: NaNh
- Task: Backlog refinement
    - Time expected: 3h
    - Time taken: 2h15m

---

# That's all folks

<div style="position:absolute;width:100%;height:100%;font-size:1vh;opacity:0.1">Send help</div>