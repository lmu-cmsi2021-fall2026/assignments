**CMSI 2021** Web Application Development, Fall 2026

# Assignment 1109
With this assignment, we fill out the stack, transitioning from using someone else’s web services to building your own. There are many ways to do this, and for this course, we have chosen [Neon](https://neon.com) to introduce you to these layers. As with any back-end development, with Neon we hope you’ll demonstrate:
* The ability to set up and configure a Neon project
* The ability to hook up a database (in this case Neon’s Postgres implementation) to a React web application
* The ability to communicate with a database through a generalized database API (in this case [PostgREST](https://docs.postgrest.org/en/stable/index.html), as provided by Neon)

## Background Reading
Prior resources relating to React and the web in general continue to apply for this assignment. Don’t be surprised if you continue to learn _even moar_ new techniques and technologies that apply to React and web apps overall (_ahem_ CSS _ahem_)

Neon’s documentation is not written for learners, unfortunately: they assume that readers already understand the overall concepts behind building a database-backed web application. Many of their examples also use tech stacks that are different from what we are using here. However, they are authoritative, so they are link to here as a reference: https://neon.com/docs. They will come across as “advanced reading” in the early stages, but as such they do make for a good “heat check” on how well you understand the material and technology by the end of the class 

That said, some Neon documentation pages are more applicable to us at our level than others. These are worth a scan:
* [Getting started with Neon Data API](https://neon.com/docs/data-api/get-started): You can follow this pretty closely, but for the “Connect and Query” section, note that we will be using **Option 2: Direct HTTP requests** rather than Option 1
* [Use Managed Better Auth with React](https://neon.com/docs/auth/quick-start/react): This works well to get you started with using Neon’s authentication service in a way that aligns with the course’s content so far

The documentation that may be of most direct use are those for [PostgREST](https://docs.postgrest.org/en/stable/references/api.html)—the generalized database web service API hosted by Neon—and SQL itself, for which [this quick crib sheet](https://neon.com/docs/postgresql/query-reference) may get you started

## For Submission
Create a blog web app using Neon for persistence plus Neon’s managed Better Auth service for authentication. You have been given a starter/sample bare-bones blog app project but you are under no obligation to use that code as given—feel free to pick and choose from it to build a blog app your way. The one thing to retain from the sample code is the _abstraction layer_ that it illustrates. Keep that, but build out everything else as you see fit. Make it as amazing as can be in terms of features and look-and-feel. Explore the possibilities—unleash your creativity!

For the database back end, note that there is an abstraction layer there as well! Make sure to create an `api` schema that lets you control PostgREST API’s endpoints in a manner that is distinct from your true table names (especially the relational convention of singular names of tables vs. the REST API convention of plural names for collections)

Make sure that your blog app goes _well beyond_ the given bare-bones version: note that this is _not_ a suggestion; it’s a requirement 😈 Some ideas:
* Expand article data: lots of potential here, such as adding tags, categories, loglines, sectioning, etc.—all of these will require additional table columns and possibly additional tables
* Filter/search articles: welcome to the world of [querying](https://docs.postgrest.org/en/stable/references/api/tables_views.html#read)
* Categorize/group articles: yes, still querying, with some [ordering](https://docs.postgrest.org/en/stable/references/api/tables_views.html#ordering) and [limits](https://docs.postgrest.org/en/stable/references/api/pagination_count.html)
* Page through articles: [actually a necessity](https://docs.postgrest.org/en/stable/references/api/pagination_count.html) as your article counts grow—with some interesting user interface options though, ranging from classic previous/next buttons to [infinite scroll](https://blog.logrocket.com/3-ways-implement-infinite-scroll-react/) (skip the third-part library option—you can build it yourself!)
* Update articles: API requests that update data typically use the `PATCH` method/verb, and [PostgREST is no exception](https://docs.postgrest.org/en/stable/references/api/tables_views.html#update)
* Delete articles: correspondingly, you’ll want [`DELETE` requests](https://docs.postgrest.org/en/stable/references/api/tables_views.html#delete) for this
* Allow photo uploads or attachments: you will want to learn about [Neon Object Storage](https://neon.com/docs/storage/overview) on the back end and [file access](https://developer.mozilla.org/en-US/docs/Web/API/File_API/Using_files_from_web_applications) on the front end
* Add user metadata (e.g., photos, profile, links, etc.): just a specific case of expanding your database structure, but this one may involve [additional columns and tables](https://neon.com/docs/postgresql/query-reference)
* Implement rich text editing: this one may require a [third-party library](https://github.com/JefMari/awesome-wysiwyg-editors) but may be worth it

Add _at least three (3)_ features beyond what is provided by the starter blog app. Additional features above and beyond these will earn extra credit based on the sophistication of those features

In all cases, provide a _db/schema.sql_ file that captures your database’s structure in its entirety. The _Copy create statements_ button in the Neon console can help here: it can be found in the Structure section of each table in your database. For additional database assistance, please add the instructor’s and TA’s Neon emails to your Neon account via the _People_ section of the Neon console so that we can access your respective projects directly

As you can see above, starter links for these features are provided but don’t hesitate to find others. As always, if you use any content directly from a source, _make sure to credit the source_. Note also that there isn’t enough time to cover all of these in class so some self-study will be called for. This is by design because it corresponds to what one typically does in industry or research.

> Although Neon provides a _client library_ to abstract out the inner details of interacting with Postgres and expose Postgres functionality to your web app by way of objects and functions, the approach used in class involves direct web requests with Neon’s PostgREST layer. This is done to reinforce prior material on web services and to emphasize that ultimately, database access over the web _is_ “just another API.” By abstracting out the database functionality away from the rest of your app code, the hope is that you will learn how to _make_ such client libraries, as opposed to being strictly a client library user.

As before, continue to reinforce and build upon the skills you have already learned:
* Retrieval from and interaction with the Neon back end
* Abstraction of Neon operations behind objects and functions (async where appropriate)
* Appropriate user interface feedback for operations-in-progress
* Graceful error handling with messaging to the user when appropriate
* Responsive layout: It must look good on a narrow or wide screen
* Site balance and aesthetics: Make it a blog app that people will want to keep visiting!

We continue the theme of requiring all-or-nothing items, to capture the range of technologies and techniques that we want to practice multiple times, in different contexts:
* A background image or gradient
* Grid layout for one or more components
* Flex layout for one or more components
* A nice title (perhaps an `h1` element, with matching CSS)
* A fun image or two (outside of the actual blog content)
* At least one transition (easiest done via `:hover` but there are other ways; and ideally something that is relevant to the user experience, not just ornamental)

These CSS properties are not required but keep them in your radar in case your particular app can use them:
* `animation`
* `border`
* `border-radius`
* `box-shadow`
* `display`
* `font-size`
* `font-weight`
* `font-style`
* `margin`
* `opacity`
* `padding`
* `position` (particularly `position: absolute` or `position: sticky`)
* `transform`
* `text-align`
* `text-shadow`

Note a few additions since last time. As before, we haven’t seen all of these in class—but they can be looked up!

Revise the boilerplate _README.md_ Markdown file to describe your blog app. Make sure to _state and elaborate on the three (3) or more features_ that go beyond the bare bones starter/sample code. Also include a clickable link to the web app deployment on GitHub Pages, and credit any notable sources if applicable

## Step-by-Step Walkthrough: Making the Starter Blog App “Go Live”
To provide you with something grounded and specific, this section takes you through the steps involved with connecting the starter blog app to a Neon project. Just like with a web app dev setup, there is no single way to do this, but when you’re starting out, it’s helpful to have something concrete to follow

### Neon project setup
1. Go to https://neon.com to acquire your Neon account. The **GitHub** option is the most convenient way to get started
2. Create a Neon project. At a minimum you’ll want the _Postgres database_ and _Better Auth_ services. _Object storage_ can be activated later if you want to take a crack at picture or other file uploads
    * Opt out of any invitations to use AI—you’re learning now, not working 🧐
3. In the _Postgres database > Data API_ section, click the **Enable Data API** button
4. In the _Postgres database > Roles_ section, check to see if you see all of these listed. The first three are created upon enabling the Data API so may take a moment to appear:
    * `authenticator`
    * `anonymous`
    * `authenticated`
    * `neondb_owner`

### Database setup
1. In the _Postgres database > Tables_ section, create the `article` table. You may do this with their interactive editor but for full replicability, SQL lets you specify things fully (you’re supposed to submit a _schema.sql_ file anyway, so you’ll eventually get here regardless). For the latter, use _Postgres database > SQL Editor_ to write and execute SQL statements such as:
```sql
CREATE TABLE article (
  id    bigint GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
  title text NOT NULL,
  body  text NOT NULL,
  date  timestamptz NOT NULL DEFAULT now()
);
```
2. Neon requires something called _row-level security_ to allow API access. There are interactive ways to do this, but again we can rely on SQL for full replicability:
```sql
ALTER TABLE article ENABLE ROW LEVEL SECURITY;
CREATE POLICY anonymous_read ON article FOR SELECT TO anonymous USING (true);
CREATE POLICY anonymous_insert ON article FOR INSERT TO anonymous WITH CHECK (true);
```
3. If you wish, you can seed your database with starter data. You can also start from scratch—every great app starts empty sometime!—but it’s also convenient to see something right away once you connect your web app. For fun, this is the same content that is hardcoded in memory on the starter blog app:
```sql
INSERT INTO article (title, body, date) VALUES
  (
    'There’s a fair tomorrow',
    E'Is a mháithrín an ligfidh tú chun aonaigh mé\nIs a mhuirnín óg ná healaí é\nBeidh aonach amárach in gContae an Chláir\nCén mhaith domh é ní bheidh mé ann',
    '2021-03-16'
  ),
  (
    'Hello Everyone',
    repeat(E'It is a good day to learn React and Firebase\n', 10),
    '2021-10-24'
  );
```

### Back-end API abstraction layer setup
Although not a requirement in general, for the purposes of the course, we want to define a separate _schema_ that captures what gets “published” to the Data API. This carries on the concept of abstraction that has threaded through this and the prior web app. As a concrete example of the utility of such abstraction, we will make sure that our database table retains a singular name `article` per relational database conventions while the Data API exposes it as plural, per [RESTful](https://aws.amazon.com/what-is/restful-api/) web service conventions. This is done by making the `api` schema refer to the `article` table (singular) with an `articles` view (plural)

1. In _Postgres database > SQL Editor_, paste and run the following SQL:
```sql
CREATE SCHEMA api;
CREATE VIEW api.articles WITH (security_invoker = true) AS SELECT * FROM article;

GRANT USAGE ON SCHEMA public TO anonymous;
GRANT USAGE ON SCHEMA api TO anonymous;
GRANT SELECT, INSERT ON article TO anonymous;        -- the view's caller needs base-table rights
GRANT SELECT, INSERT ON api.articles TO anonymous;
```
2. In _Settings > Postgres > Data API_, click on the _Show advanced_ switch. In the _Exposed schemas_ dropdown, uncheck the `public` schema and check the `api` schema. Save your changes
3. Whenever you do anything that affects what will be visible via the Data API, you want to refresh it. The SQL above is one case, but most of the time this will be when you modify your tables. Refreshing the API is a matter of going to _Postgres database > Data API_ and clicking the **Refresh schema cache** button

### Web app setup
You’re now ready to get your web app to talk to your database! Rather than give you fully-formed sample code, this is described as individual steps so that you can do them more deliberately and thus learn them better:
1. You will be creating a file that contains settings which _must not be committed_. As such, edit the _.gitignore_ file and add `.env` to the list of files and patterns therein. Commit this change
2. Create the _.env_ file. This will have two lines, defining _environment variables_ which your web app will use:
```
VITE_NEON_AUTH_URL=https://ep-xxxxx.neonauth.c-2.us-east-1.aws.neon.tech/neondb/auth
VITE_NEON_DATA_API_URL=https://ep-xxxxx.apirest.c-2.us-east-1.aws.neon.tech/neondb/rest/v1
```
3. Note the values on the right of the `=` signs show you how the real values will generally look but you will need to paste the actual values yourself because they pertain to your project specifically
4. Click the green **Connect** button in your Neon console and paste the _Auth > Auth URL_ value as your `VITE_NEON_AUTH_URL` environment variable
5. Paste the _Data API > API URL_ value as your `VITE_NEON_DATA_API_URL` environment variable

### Your first database access code
Finally! You’re almost there. Note how these instructions change the _articleService.js_ file and _nothing else_. Again, abstraction! Your final file organization may vary (for example, you might want to separate some of this code into constants or utilities files) but the point to get across here is that proper structuring of your code will _shield the rest of your app_ from database- and API-specific details. The only changes that would propagate to your components are those that affect the actual _content_ of your database, such as additional columns or tables

Some of the code fragments given here require additional knowledge that we will need to elide for now. Just copy those as-is and make a mental note to ask about those later if you really want to dig in deeper:
1. Read the environment variables into JavaScript constants. While we’re at it, let’s also define the base endpoint for accessing articles. You guessed it, PostgreSQL defines an endpoint for each table or view in the schema that it publishes (in this case, `api`):
```javascript
const DATA_API_URL = import.meta.env.VITE_NEON_DATA_API_URL
const AUTH_URL = import.meta.env.VITE_NEON_AUTH_URL

const ARTICLES_ENDPOINT = `${DATA_API_URL}/articles`
```
2. Before we write the request code, we’ll need a small utility function to check for errors. This avoids unnecessary duplication for basic response success checks. You can customize the error message to taste as you build your app further later:
```javascript
async function checkResponse(response) {
  if (!response.ok) {
    throw new Error(`${response.url} ${response.status}: ${await response.text()}`)
  }

  return response.json()
}
```
3. Even for anonymous access, you still need to _authenticate_ with the server. Authenticating gives you a _token_ (the authorization kind, not the AI kind) that you then use in future requests. The token expires so future requests may need to authenticate again; here we just reauthenticate since we’re anonymous anyway, but having an actual login may change this. This part has some of the aforementioned “gory details” that we’ll elide for now—but note the `fetch` call and the `async`/`await` structure with which you should now be pretty familiar:
```javascript
let anonymousToken = null

function extractExpiration(token) {
  const payload = JSON.parse(atob(token.split('.')[1].replace(/-/g, '+').replace(/_/g, '/')))
  return payload.exp * 1000
}

async function getAnonymousToken() {
  if (!anonymousToken || Date.now() > anonymousToken.expiresAt - 60_000) {
    const { token } = await checkResponse(await fetch(`${AUTH_URL}/token/anonymous`))
    anonymousToken = { token, expiresAt: extractExpiration(token) }
  }

  return anonymousToken.token
}
```
4. One more network utility function before we get to the services! Invocations of the Data API all follow a top-level pattern: check for a token, get one if we don’t have it, then use it to make the actual request. To avoid copy-pasting this all of the time, we put it in a `dataApiRequest` function. Note how the token is passed—it’s a new _header_ for the request, called `Authorization` and starting with the word `Bearer` followed by the token supplied by the authentication endpoint:
```javascript
async function dataApiRequest(url, { headers, ...options } = {}) {
  if (!DATA_API_URL || !AUTH_URL) {
    throw new Error('VITE_NEON_DATA_API_URL and VITE_NEON_AUTH_URL must be set (see .env.example)')
  }

  const token = await getAnonymousToken()
  return checkResponse(await fetch(url, { ...options, headers: { ...headers, Authorization: `Bearer ${token}` } }))
}
```
5. And now…the service functions. This is where we finally wipe out the hardcoded implementation and go live completely. We must preserve the arguments and return value of course—that’s what maintains the abstraction. It’s only when you add more functionality or change content that updates have to propagate to your React components. We include one last utility function here: a simple row “converter” that replaces the returned date strings with actual JavaScript `Date` objects:
```javascript
// Postgres sends timestamptz values as ISO strings; the components expect a Date.
const rowToModel = row => ({ ...row, date: new Date(row.date) })

export async function createArticle({ title, body }) {
  // The id and date are generated by the database; `Prefer: return=representation`
  // asks PostgREST to send the inserted row back so we can return the full article.
  const [row] = await dataApiRequest(ARTICLES_ENDPOINT, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json', Prefer: 'return=representation' },
    body: JSON.stringify({ title, body })
  })

  return rowToModel(row)
}

export async function fetchArticles() {
  const rows = await dataApiRequest(`${ARTICLES_ENDPOINT}?order=date.desc`)
  return rows.map(rowToModel)
}
```

### Run, Rinse, & Repeat
All the pieces should now be in place: `npm run dev` and try things out! As you add articles to the blog app, watch the `article` table in the Neon console to confirm that the database is online. Once you get here, what’s next is up to you!

## Operational Tips/Suggestions
* Note again that the wealth of possibilities means that self-study and experimentation are built into the work involved with this assignment. Make sure to plan accordingly!
* Take advantage of the very distinct layers involved here: the back end (Neon) and the front end (React). To keep the learning manageable, try to look at each layer in isolation—see if you can first get the Neon side to work without any visual interface, possibly just printing things and/or inspecting the console. _Then_ build the user interface on top of it knowing that the back end functionality already works. Or vice versa, if the user interface part looks tricker
* You may make mistakes, change your mind about features, or run into a dead end, all of which will take time—ideally, _build that time in_ when planning out how you will work on the app
* Setup of Prettier has been shown in class, so there is no reason at this point for why your code (all files) wouldn’t be flawlessly formatted, with 100% consistent indentation and spacing, and perfectly consistent blank-line spacing where necessary. Activate “format-on-save” if your editor has it, so you don’t have to ever worry about formatting while working
* Many operational tips and suggestions from the past assignments also still apply—don’t hestitate to review them!

## How to Turn it In
* Commit your code to a GitHub repository within the [lmu-cmsi2021-fall2026](https://github.com/lmu-cmsi2021-fall2026) organization with the following naming convention: `database-backed-username`, where _username_ is your GitHub handle
* Add the instructor and TA’s Neon emails to your project, so that we can help with database-side issues
* Include a _db/schema.sql_ file that captures your database structure completely in SQL, so that it can be recreated programmatically
* Update the _README.md_ file with a description of your blog app and the three (3) or more features that you implemented and including a clickable link to the web app deployment on GitHub Pages plus source credits if applicable
* Make sure that your deployment is live and functional at https://lmu-cmsi2021-fall2026.github.io/database-backed-username/ (again with _username_ being your GitHub handle)

## Specific Point Allocations
For this particular assignment, graded categories are as follows:

| Category | Points |
| -------- | -----: |
| Baseline functionality | 12 points total |
| • Authentication | 4 points |
| • Database (including _db/schema.sql_) | 4 points |
| • API layer | 4 points |
| Three (3) features beyond Bare Bones Blog | 12 points each, 36 points total |
| Baseline code quality | 16 points total |
| This is a composite score indicating how successfully the code has:<br/>• Fully-abstracted service modules<br/>• Warning- and error-free developer console | |
| Design & usability | 18 points total |
| This is a composite score indicating how successfully the app demonstrates:<br/>• Responsive design<br/>• Effective aesthetic choices<br/>• Helpful feedback, especially when waiting for asynchronous operations<br/>• Graceful error handling (e.g., when a network request fails) | |
| Implementation specifications | 10 points—all or nothing |
| • Background image or gradient<br/>• Grid layout<br/>• Flex layout<br/>• Title<br/>• Fun image(s)<br/>• Transition | |
| Blog app description in _README.md_ | 8 points total |
| • About the three (3) added features | 6 points |
| • Clickable link to app deployment | 2 points |
| • Credits where appropriate | deduction only (if not done) |
| Hard-to-maintain or error-prone code | deduction only |
| Hard-to-read code | deduction only |
| Version control | deduction only |
| Punctuality | deduction only |
| **Total** | **100** |

Note that inability to compile and run any code to begin with will negatively affect other criteria, because if we can’t run your code, we can’t evaluate related remaining items completely
