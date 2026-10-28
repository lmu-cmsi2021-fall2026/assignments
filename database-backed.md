**CMSI 2021** Web Application Development, Fall 2026

# Assignment 1109
With this assignment, we fill out the stack, transitioning from using someone else’s web services to building your own. There are many ways to do this, and for this course, we have chosen [Neon](https://neon.com) to introduce you to these layers. As with any back-end development, with Neon we hope you’ll demonstrate:
* The ability to set up and configure a Neon project
* The ability to hook up a database (in this case Neon’s Postgres implementation) to a React web application
* The ability to communicate with a database through a generalized database API (in this case [PostgREST](https://docs.postgrest.org/en/stable/index.html), as provided by Neon)

## Background Reading
Prior resources relating to React and the web in general continue to apply for this assignment. Don’t be surprised if you continue to learn _even moar_ new techniques and technologies that apply to React and web apps overall (_ahem_ CSS _ahem_)

Neon’s documentation is not written for learners, unfortunately: they assume that readers already understand the overall concepts behind building a database-backed web application. Many of their examples also use tech stacks that are different from what we are using here. However, they are authoritative, so they are linked to here as a reference: https://neon.com/docs. They will come across as “advanced reading” in the early stages, but as such they do make for a good “heat check” on how well you understand the material and technology by the end of the class 

That said, some Neon documentation pages are more applicable to us at our level than others. These are worth a scan:
* [Getting started with Neon Data API](https://neon.com/docs/data-api/get-started): You can follow this pretty closely, but for the “Connect and Query” section, note that we will be using **Option 2: Direct HTTP requests** rather than Option 1
* [Use Managed Better Auth with React](https://neon.com/docs/auth/quick-start/react): This works well to get you started with using Neon’s authentication service in a way that aligns with the course’s content so far

The documentation that may be of most direct use are those for [PostgREST](https://docs.postgrest.org/en/stable/references/api.html)—the generalized database web service API hosted by Neon—and SQL itself, for which [this quick crib sheet](https://neon.com/docs/postgresql/query-reference) may get you started

## For Submission
Create a blog web app using Neon for persistence plus Neon’s managed Better Auth service for authentication. You have been given a starter/sample bare-bones blog app project but you are under no obligation to use that code as given—feel free to pick and choose from it to build a blog app your way. The one thing to retain from the sample code is the _abstraction layer_ that it illustrates. Keep that, but build out everything else as you see fit. Make it as amazing as can be in terms of features and look-and-feel. Explore the possibilities—unleash your creativity!

For the database back end, note that there is an abstraction layer there as well! Make sure to create an `api` schema that lets you control PostgREST API’s endpoints in a manner that is distinct from your true table names (especially the relational convention of singular names of tables vs. the REST API convention of plural names for collections)

Make sure that your blog app goes _well beyond_ the given bare-bones version: note that this is _not_ a suggestion; it’s a requirement 😈 Some ideas:
* _Support multiple “pages” with React Router:_ Although not strictly database-related, React Router’s nested path and `Outlet` capabilities correspond quite well to displaying individual items embedded within a list display or for navigating between login/signup and content views
* _Expand article data:_ Lots of potential here, such as adding tags, categories, loglines, sectioning, etc.—all of these will require additional table columns and possibly additional tables
* _Filter/search articles:_ Welcome to the world of [querying](https://docs.postgrest.org/en/stable/references/api/tables_views.html#read)
* _Categorize/group articles:_ Yes, still querying, with some [ordering](https://docs.postgrest.org/en/stable/references/api/tables_views.html#ordering) and [limits](https://docs.postgrest.org/en/stable/references/api/pagination_count.html)
* _Page through articles:_ [Actually a necessity](https://docs.postgrest.org/en/stable/references/api/pagination_count.html) as your article counts grow—with some interesting user interface options though, ranging from classic previous/next buttons to [infinite scroll](https://blog.logrocket.com/3-ways-implement-infinite-scroll-react/) (skip the third-party library option—you can build it yourself!)
* _Update articles:_ API requests that update data typically use the `PATCH` method/verb, and [PostgREST is no exception](https://docs.postgrest.org/en/stable/references/api/tables_views.html#update)
* _Delete articles:_ Correspondingly, you’ll want [`DELETE` requests](https://docs.postgrest.org/en/stable/references/api/tables_views.html#delete) for this
* _Allow photo uploads or attachments:_ You will want to learn about [Neon Object Storage](https://neon.com/docs/storage/overview) on the back end and [file access](https://developer.mozilla.org/en-US/docs/Web/API/File_API/Using_files_from_web_applications) on the front end
* _Add user metadata (e.g., photos, profile, links, etc.):_ Just a specific case of expanding your database structure, but this one may involve [additional columns and tables](https://neon.com/docs/postgresql/query-reference)
* _Implement rich text editing:_ This one may require a [third-party library](https://github.com/JefMari/awesome-wysiwyg-editors) but may be worth it

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
To provide you with something grounded and specific, this section takes you through the steps involved with connecting the starter blog app to a Neon project. Just like with a web app dev setup, there is no single way to do this, but when you’re starting out, it’s helpful to have something concrete to follow. And also like the web app dev setup steps, each phase holds knowledge to gain so that you can apply this with different tech stacks in the future

### Neon project setup
1. Go to https://neon.com to acquire your Neon account. The **GitHub** option is the most convenient way to get started
2. Create a Neon project. At a minimum you’ll want the _Postgres database_ and _Better Auth_ services. _Object storage_ can be activated later if you want to take a crack at picture or other file uploads
    * Opt out of any invitations to use AI—you’re learning now, not working 🧐
3. In the _Postgres database > Data API_ section, click the **Enable Data API** button
4. Next, in the _Better Auth_ section, click the **Configure Auth** button
5. You don’t have to do anything at that configuration page, but after visiting it, in the _Postgres database > Roles_ section you should now see all of these listed:
    * `authenticator`
    * `anonymous`
    * `authenticated`
    * `neondb_owner`

**Test your understanding:** “Where” are these setup steps taking place? And _when_ are these setup steps required: every work session? For every new feature? For every new app?

**Check your work:** Log in and out of Neon, or access Neon through a private/incognito browser window. Your project and settings should still be there. Create and delete as many projects as you like, to get the hang of the process

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
2. Neon expects every exposed table to have _row-level security_: enabling it denies all access until policies explicitly allow it, which is what the two policies below do. There are interactive ways to do this, but again we can rely on SQL for full replicability:
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

**Test your understanding:** Consider this statement: “The Neon console is itself a database-backed web app.” Would you agree or disagree? What makes it different from the web app that you’re about to build? What makes it similar?

**Check your work:** Go back and forth between doing things in the Neon console interactive tools vs. SQL (the code fragments above create entities and add data, but [Neon’s Postgres query reference](https://neon.com/docs/postgresql/query-reference) shows more possibilities). Take note of how SQL statements impact what the interactive tools show and vice versa. Seek to gain an understanding of how one affects the other

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

**Test your understanding:** Aside from the singular/plural naming difference, can you think of other ways that having a distinct `api` schema would help in making table and data management easier? Can you think of potential consequences of skipping a separate schema and just exposing the `public` schema entirely?

…OK, those may be trick questions because they are harder to answer without spending more time working with the API (the next two sections). So, here’s something more foundational: what the heck is a “schema” anyway? After exploring the Neon console and seeing how schemas relate to tables, can you think of analogous concepts or structures in computing?

**Check your work:** Just like with the database setup, see how/if these SQL statements visibly affect the Neon console’s interactive displays of tables, schemas, permissions, and roles. Do these changes show up? Do you see concrete connections between what you do on the Neon console interactively and what SQL statements may correspond to them?

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

_Protip:_ In full-blown dev setups, there may be multiple _.env*_ files for different environments, and in that case the filename _.env.local_ designates the specific settings to be used exclusively on the machine that it is on. We elided that here for simplicity, but if you wish to mimic that you are free to do so

**Test your understanding:** Look up the term “environment variable:” they are relevant in multiple contexts, and a solid understanding of the concept will serve you well in the future. For those of you who _have_ encountered environment variables before (and I know for a fact that some of you have 🛠️🪚🪛), yes these are the same things—though perhaps you are seeing them set in this manner for the first time

As for the _.env_ file itself, why is this something that you should _not_ commit? Don’t just leave this as IYKYK—make sure you _do_ know. Some of you do, based on past classes 🛠️🪚🪛 but if this stumps you, look it up or ask the instructor

**Check your work:** Verify that the web app can see these variables! Stick the following temporary `console.log` invocations right before the `App` component’s `return` statement to confirm that the values you entered show up in the app:
```javascript
console.log(import.meta.env.VITE_NEON_AUTH_URL)
console.log(import.meta.env.VITE_NEON_DATA_API_URL)
```

Also make sure that your _.gitignore_ edit did work correctly: `git status` should never show the _.env_ file, no matter how much you modify it

### Your first database access code
Finally! You’re almost there. Note how these instructions change the _articleService.js_ file and _nothing else_. Again, abstraction! Your final file organization may vary (for example, you might want to separate some of this code into constants or utilities files) but the point to get across here is that proper structuring of your code will _shield the rest of your app_ from database- and API-specific details. The only changes that would propagate to your components are those that affect the actual _content_ of your database, such as additional columns or tables

Some of the code fragments given here require additional knowledge that we will need to elide for now. Just copy those as-is and make a mental note to ask about those later if you really want to dig in deeper:
1. Read the environment variables into JavaScript constants. While we’re at it, let’s also define the base endpoint for accessing articles. You guessed it, PostgREST defines an endpoint for each table or view in the schema that it publishes (in this case, `api`):
```javascript
const AUTH_URL = import.meta.env.VITE_NEON_AUTH_URL
const DATA_API_URL = import.meta.env.VITE_NEON_DATA_API_URL

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
4. Now that you see what the token response looks like, we can do one more network utility function before we get to the services. Invocations of the Data API all follow a top-level pattern: check for a token, get one if we don’t have it, then use it to make the actual request. To avoid copy-pasting this all of the time, we put it in a `dataApiRequest` function. Note how the token is passed—it’s a new _header_ for the request, called `Authorization` and starting with the word `Bearer` followed by the token supplied by the authentication endpoint:
```javascript
async function dataApiRequest(url, { headers, ...options } = {}) {
  if (!DATA_API_URL || !AUTH_URL) {
    throw new Error('VITE_NEON_DATA_API_URL and VITE_NEON_AUTH_URL must be set (see .env)')
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

**Test your understanding:** Try these endpoints in Postman! Note that the final endpoint in the `getAnonymousToken` function’s `fetch` call is `AUTH_URL` followed by `/token/anonymous`. Do this request live in Postman and take note of the response that you get

Once you have a firsthand feel for the authentication endpoint, move on to the data endpoints. Doing these manually—a few times, in fact, so that it settles into your brain—will help you understand what the code is doing more deeply. First, acquire a token with the authentication endpoint. Copy the `token` from the response then include it in a _new_ request (the `ARTICLES_ENDPOINT` URL will do just fine), making sure to add a _header_ called `Authorization` whose value is `Bearer ` followed by that exact token (note the space in between). Get to know the response. What happens when you don’t include the `Authorization` header? What happens when you use an expired token?

For the article creation endpoint, note now that this is a `POST` request rather than a `GET`. Note also the additional `Content-Type` and `Prefer` headers. The `{ title, body }` object goes in the request’s body. Even better, if this request reports success, go back to the Neon console to see what happened. Anticipate the change that would be made, then navigate to the appropriate section of the console to verify if you predicted that correctly

Doing these requests manually in Postman is a key action toward gaining a full understanding of the process: this way, you understand the code deeply because you know how to do it yourself _by hand_. And we don’t mean writing the code by hand, but _actually making the request_ by hand. We can’t overemphasize how helpful that is in fostering deep comprehension of what’s going on under the hood

**Check your work:** Now that you know what happens by hand, see if your code does the same. Include a temporary `useEffect` or event handler in your code that calls either exported service function (just hardcode the arguments to make it a quick check). Do you see the request in the Network debug tool, and does the response match your expectation? What happens if you temporarily take the network offline and you call those functions? Do you see how our prior implementation techniques for API-backed web apps apply to these service functions?

### Test suite mock setup
After all that, we have one cleanup detail before allowing ourselves to experiment freely—we don’t have enough time in the course to address web app unit tests, but it’s important to point one thing out at this juncture: unit tests should _not_ connect to live services! Imagine having a huge dev team, human or otherwise, cranking away at your code…the accumulated test runs on a live service could very well run up huge service bills and capacity limits. Instead, you want to _mock_ those services so that they provide artificial, in-memory responses:
1. Edit the _App.test.jsx_ file so that it now also imports `vi` (for _vitest_, not the command-line editor):
```javascript
import { test, vi } from 'vitest'
```
2. After the `import` statements, insert this mock code:
```javascript
// The real service talks to the Neon Data API over the network, so stand in a fake one.
vi.mock('../services/articleService', () => ({
  fetchArticles: async () => [],
  createArticle: async ({ title, body }) => ({ id: 1, title, body, date: new Date() })
}))
```

**Test your understanding:** At this level, we just want to avoid the possibility of hitting a service live when running the app’s test suite, so it suffices that you know _why_ we would want to do this. But there’s a lot more to unpack here that we just don’t have time to spell out within the course. Let me know if you’re curious about how this all works

A key notion here is that the `mock` being done above is completely _minimal_: it simulates an empty blog and always returns the same `id` when “creating” a new article. More sophisticated mocks can be created so that they simulate behavior that tests your components more closely. Not surprisingly, such mocks may have sample data and additional functionality…not unlike the hardcoded implementation of the original starter code. That’s another hidden value-add within that repository: it provides a hint for what more sophisticated mocks might look like

**Check your work:** The main check here is to make sure that `npm run test` doesn’t open network connections. However, that’s hard to verify unless you know how to use network monitoring tools, so for now you’ll have to trust that the above code does indeed avoid hitting up Neon for real

### Run, Rinse, & Repeat
All the pieces should now be in place: `npm run dev` and try things out! As you add articles to the blog app, watch the `article` table in the Neon console to confirm that the database is online. Once you get here, what’s next is up to you! (though you most likely want to proceed to the next walkthrough)

## Another Step-by-Step Walkthrough: Auth All the Things
If you followed the previous walkthrough closely and accurately, your blog app now happily loads and adds blog posts to a live Neon database, with articles stored permanently across however many browser sessions or machines you use. However, it’s wide open! Anyone and everyone can post articles, and you have no idea who they are

This walkthrough now shows you how to add _authentication_ to your app. For this, Neon provides its [managed _Better Auth_ service](https://neon.com/docs/auth/overview). This service is meant to provide turnkey, out-of-the-box ready logins and users: for developers, this just means “connect and go.” The service is “managed” because Neon runs the software and maintains the servers hosting the software—i.e., they are managing it for you. You can download, run, and host the [Better Auth library](https://better-auth.com) yourself…but you have better things to do! In that sense, their database is a managed service as well: you _could_ install and host your own [PostgreSQL](https://www.postgresql.org) database with a [PostgREST](https://postgrest.org) API server on top of it, but that’s exactly what Neon does for you, so that you can hop straight to writing web apps that use these technologies

For an initial taste of Better Auth, you can follow Neon’s [React quick start](https://neon.com/docs/auth/quick-start/react) as an initial exercise. The activities and code in this walkthrough are based on that quick start, but (a) adapted to the starter blog web app and (b) expanded so that articles are now attributable to the logged-in users that created them

### Neon Auth setup
As a preflight check, make sure that the Data API and Better Auth services are ready to go: in _Postgres database > Data API > Security_, confirm that “Neon Auth is ready” is checked. If not, click the _Neon Auth_ button to activate it

### Neon SDK setup
Like PostgREST, it is possible to interact with Better Auth purely via `fetch` requests: yes, it is “just another web service.” However, the interactions are sufficiently complex that we’d rather not write this all ourselves. For this, we need Neon’s SDK

Note that we are taking the opposite approach here from database access. There _are_ convenience functions available for use with the database. But from a learning perspective, we have chosen to expose you to both. Pure PostgREST interaction via `fetch` is fairly straightforward, but Better Auth (and authentication in general) isn’t. This difference drives the choices made here

This part is a single step, an `npm` invocation to be done while `cd`’ed within your local repository folder:
```
npm install @neondatabase/neon-js@latest
```

**Test your understanding:** Can you think of other factors that may inform the decision of whether to interact with a system natively (e.g., at the level of `fetch`) or to utilize a library/SDK that abstracts these functions out for you? (_Hints:_ There’s that “abstract” word again! In addition, do an `npm run build` both before and after completing this walkthrough…see if you can spot a difference)

**Check your work:** See if you can import `createAuthClient` without errors. A throwaway `console.log` should suffice in verifying its presence:
```javascript
import { createAuthClient } from '@neondatabase/neon-js/auth'

console.log(createAuthClient)
```
You should then see something like this on the browser dev tool Console tab:
```
ƒ createAuthClient(url, config) {
	return createInternalNeonAuth(url, config).adapter;
}
```

### Web app sign-up, sign-in, and sign-out setup
This part will feel like the most substantive change, and it’s also the most open-ended one: that’s because it involves integrating a sign-up, sign-in/login, and sign-out/logout flow into the web app itself. There are _tons_ of ways to do this: the code here is by no means authoritative. You’ll probably want to redo this your way

The purpose of this particular approach is (a) to get this workflow going as quickly as possible and (b) to keep it as similar as possible to Neon’s own [React quickstart for managed Better Auth](https://neon.com/docs/auth/quick-start/react). So again, the most important part of this walkthrough is that you _understand_ how things connect so that you can then revise it into how you actually want it to be

The overall idea here is to “gate” the main blog component behind a login: users can’t get to the blog until they sign-up and login. This in itself has variants: you might want anyone to _read_ the blog but not _write_ to it unless they have signed up. Again, that’s why it’s important to understand what’s happening here vs. keeping the code wholesale:
1. The `App` component will now change into a “gatekeeper” that will show the blog if a user is logged in, but provide a sign-in/login user interface if the user isn’t there. Because `App` is currently the blog itself, we want to move that out to a different component, with `App` holding just the logic that chooses between the blog and sign-in/login. As such, we want to:
    * Copy _App.jsx_ and _App.css_ into new files _Blog.jsx_ and _Blog.css_
    * In _Blog.jsx_, replace all references and names pertaining to `App` into something closer to `Blog`: definitely the component’s name, plus its top-level CSS class name. There may be more but you’ll want at least those for sure
2. Next, you’ll want to create a `LoginSignup` component to ask for a user’s email and password. For connectivity of reference, the code in this walkthrough closely resembles [Neon’s quickstart](https://neon.com/docs/auth/quick-start/react), with some key tweaks that we’ll get to momentarily. And yes, it’s somewhat long 😅
```jsx
import { useState } from 'react'

import './LoginSignup.css'

export default function LoginSignup({ onSignUp, onSignIn }) {
  const [email, setEmail] = useState('')
  const [password, setPassword] = useState('')
  const [isSignUp, setIsSignUp] = useState(true)

  const handleSubmit = async event => {
    event.preventDefault()

    try {
      if (isSignUp) {
        await onSignUp({ name: email.split('@')[0] || 'User', email, password })
      } else {
        await onSignIn({ email, password })
      }
    } catch (error) {
      alert(error.message)
    }
  }

  return (
    <form className="LoginSignup" onSubmit={handleSubmit}>
      <h1>Welcome to the Bare Bones Blog 🦴</h1>
      <h2>{isSignUp ? 'Sign Up' : 'Sign In'}</h2>

      <input type="email" placeholder="Email" value={email} onChange={event => setEmail(event.target.value)} required />

      <input
        type="password"
        placeholder="Password"
        value={password}
        onChange={event => setPassword(event.target.value)}
        required
      />

      <button type="submit">{isSignUp ? 'Sign Up' : 'Sign In'}</button>

      <p>
        {isSignUp ? (
          <>
            Already have an account?{' '}
            <a
              href="#"
              onClick={event => {
                event.preventDefault()
                setIsSignUp(false)
              }}
            >
              Sign in
            </a>
          </>
        ) : (
          <>
            Don't have an account?{' '}
            <a
              href="#"
              onClick={event => {
                event.preventDefault()
                setIsSignUp(true)
              }}
            >
              Sign up
            </a>
          </>
        )}
      </p>
    </form>
  )
}
```
3. Note the code refers to a _LoginSignup.css_ file. Go ahead and create it, but we’ll leave the exact styling to you
4. You may have noticed that `LoginSignup` expects to be given `onSignUp` and `onSignIn` functions—we’re building toward that! You may have also noticed that one difference between `LoginSignup` and the quickstart’s app is that it has _less_ stuff than the original. That’s because, for our walkthrough, the parts that interact with Neon have been _abstracted_ (yes, that word again) into its own _authService.js_. Notice again how it resembles the parts that we took out of the quickstart app but have reorganized and renamed things to be more standalone. We also introduce here the concept of a React _hook_, which is described briefly in a comment block:
```javascript
import { useEffect, useState } from 'react'
import { createAuthClient } from '@neondatabase/neon-js/auth'

const authClient = createAuthClient(import.meta.env.VITE_NEON_AUTH_URL)

/**
 * This is new (and different from the Neon walkthrough): instead of invoking the Neon-specific
 * `authClient` directly from components, we wrap that within its own function, known in React
 * as a “hook.” Hooks are like components that have no JSX, but they can have everything else,
 * and typically return a value that components can then use. That value can have anything,
 * including functions within the hook.
 */
export const useAuthService = () => {
  const [session, setSession] = useState(null)
  const [user, setUser] = useState(null)
  const [authenticating, setAuthenticating] = useState(true)

  const updateSession = async authResult => {
    if (authResult.error) {
      setAuthenticating(false)
      throw new Error(authResult.error.message)
    }

    const sessionResult = await authClient.getSession()
    if (sessionResult.data?.session && sessionResult.data?.user) {
      setSession(sessionResult.data.session)
      setUser(sessionResult.data.user)
    }
  }

  const signUp = async ({ name, email, password }) => {
    setAuthenticating(true)

    try {
      await updateSession(await authClient.signUp.email({ name, email, password }))
    } finally {
      setAuthenticating(false)
    }
  }

  const signIn = async ({ email, password }) => {
    setAuthenticating(true)

    try {
      await updateSession(await authClient.signIn.email({ email, password }))
    } finally {
      setAuthenticating(false)
    }
  }

  const signOut = async () => {
    await authClient.signOut()
    setSession(null)
    setUser(null)
  }

  // Invoking this hook immediately checks for a current session.
  useEffect(() => {
    authClient.getSession().then(result => {
      if (result.data?.session && result.data?.user) {
        setSession(result.data.session)
        setUser(result.data.user)
      }
      setAuthenticating(false)
    })
  }, [])

  return { session, user, authenticating, signUp, signIn, signOut }
}
```
   (yes, this file should sit next to _articleService.js_ in the _services_ folder)

5. And now, the overhauled `App` component puts everything together. It imports the `useAuthService` hook that we just defined and is reduced to a decision between showing `Blog` vs. showing `LoginSignup`:
```jsx
import './App.css'

import { useAuthService } from '../services/authService'

import Blog from './Blog'
import LoginSignup from './LoginSignup'

export default function App() {
  const { session, user, authenticating, signUp, signIn, signOut } = useAuthService()

  if (authenticating) {
    return <section className="App-loading">Loading...</section>
  }

  return session && user ? <Blog onSignOut={signOut} /> : <LoginSignup onSignUp={signUp} onSignIn={signIn} />
}
```
6. Revisions to _App.css_ will also be called for but we will leave that to you. For starters, virtually everything in the original has moved to _Blog.css_, so emptying out _App.css_ completely is a good first step
7. Aaaaand…one more thing: in the code above, notice that we are now passing an `onSignOut` function prop to the `Blog` component. We want to make sure that `Blog` makes good use of that. First, make sure it reads the property:
```javascript
export default function Blog({ onSignOut }) {
```
8. Then, add a button wherever you like that will allow the user to logout. Clicking this button will clear out the current session and user, causing `App` to switch back to the `LoginSignup` component:
```jsx
<button onClick={onSignOut}>Sign Out</button>
```
9. This is pretty much “check your work:” run the app! You should now be greeted by a signup/login page rather than the blog. Better yet, _sign in_! The blog should then be visible until you logout
10. Also, do see what happens when errors occur—with authentication, you automatically have two cases: attempting to login as a non-existent user, and attempting to sign up as a user that’s already there. Don’t get your hopes up too much—this is a minimal walkthrough after all. But the code should be structured in a way that you can build better, friendlier error-handling on top of this foundation

**Test your understanding:** Well, hmmm, that was a lot 🫠 But the big takeaway is how everything _flows_. What determines whether you see signup/login vs. the blog? What changes that state (hint), and how? As mentioned by the last step, how are errors reported? Knowing these parts will allow you to transform the rudimentary code here into the user interface that you really want

Note also, this all pertains to basic email/password login, which is the default configuration for Better Auth as managed by Neon. Visit the _Better Auth_ section of the Neon console and click on _Configure Auth_ to see how else you can customize your web app’s login experience

**Check your work:** Speaking of the _Better Auth_ section, do visit it after signing up one or more users into your blog app—they should be listed there now! You can see the email you used plus other details, and you also have the option to delete them. Your project, your rules. But remember, with great power comes great responsibility 🕸️

### Test suite mock setup
As with the previous walkthrough, the addition of `useAuthService` requires that we mock it up in test code, to avoid having test suites “phone home” to Neon when they don’t have to:
1. Add this new import and mock to _App.test.jsx_:
```javascript
import { useAuthService } from '../services/authService'

// The real services talk to Neon over the network, so stand in fakes for both of them.
vi.mock('../services/authService', () => ({
  useAuthService: vi.fn(),
}))
```
2. The empty mock is nearly a baseline though—this is a good time to introduce the notion of _customizing_ those mocks depending on the situation. For example, you may want to test situations when a user is already logged in vs. not. In such cases, you would begin tests with a custom value:
```javascript
useAuthService.mockReturnValue({
  session: { token: 'test-token' },
  user: { email: 'reader@example.com' },
  authenticating: false,
  signUp: () => { /* Custom behavior, if needed */ },
  signIn: () => { /* Custom behavior, if needed */ },
  signOut: () => { /* Custom behavior, if needed */ }
})
```
3. Use `npm run test` to check the [very minimal] test suite for errors relating to `useAuthService`. If something pops up, add something similar to the code above in order to provide an applicable mock value

**Test your understanding:** In general, what kinds of changes to your code would most likely call for new mocks in your test suite?

**Check your work:** As before, you want to ensure that none of your tests “phone home” to Neon during `npm run test`. This may not have much impact given the very minimal _App.test.jsx_, but as your test coverage grows, this is something to watch out for

## One Moar Step-by-Step Walkthrough: Just Add User
At this point, your morphed blog app looks like it is now fully integrated with Neon: users can’t reach the blog until they have signed up and logged in, and articles are stored for posterity! But under the hood, it is missing one last foundational mechanism: actually _utilizing_ the current user’s information. Note how articles are still created anonymously—all you know is that one of your users wrote them. As our way of illustrating the more general functionality of taking the logged-in user into account while going about your web app’s business, we will implement _user attribution_: storing the current user’s ID alongside the articles that they create

### Database migration
Associating articles with a user ID will require adding a column to the `article` table. When structural changes such as this are made to an existing database, that database is said to be _migrated_ to a new version. You will likely migrate your database multiple times as you work on your app, so consider this to be an example of how this is done. This migration is probably more complex than those that you will do because it replaces anonymous access with user access—something you will not likely need to change after this walkthrough

1. The following SQL script adds a `user_id` column to the `article` table. It migrates already-existing articles by filling in that column with the value `seed`, for “seed data.” This is an arbitrarily chosen value and you can use anything else that is more meaningful to you. Or, you can delete all existing article rows beforehand in order to start fresh:
```sql
ALTER TABLE article ADD COLUMN user_id text;

UPDATE article SET user_id = 'seed' WHERE user_id IS NULL;  -- Marks pre-existing articles as “seed” data.

ALTER TABLE article
  ALTER COLUMN user_id SET NOT NULL,
  ALTER COLUMN user_id SET DEFAULT (auth.user_id());
```
2. This SQL fragment revokes anonymous access to your database and API:
```sql
DROP POLICY anonymous_read ON article;
DROP POLICY anonymous_insert ON article;
REVOKE ALL ON article FROM anonymous;
REVOKE ALL ON api.articles FROM anonymous;
REVOKE USAGE ON SCHEMA public FROM anonymous;
REVOKE USAGE ON SCHEMA api FROM anonymous;
```
3. Next, this SQL fragment then grants access to logged-in (authenticated) users:
```sql
CREATE POLICY authenticated_read ON article FOR SELECT TO authenticated USING (true);
CREATE POLICY authenticated_insert_own ON article FOR INSERT TO authenticated WITH CHECK (user_id = auth.user_id());

GRANT USAGE ON SCHEMA public TO authenticated;
GRANT USAGE ON SCHEMA api TO authenticated;
GRANT SELECT, INSERT ON article TO authenticated;
GRANT SELECT, INSERT ON api.articles TO authenticated;
```
4. Finally, we make sure that the API-exposed `articles` view now includes the new column:
```sql
CREATE OR REPLACE VIEW api.articles WITH (security_invoker = true) AS SELECT * FROM article;
```
5. If, after all this, you were thinking that you should click the **Refresh schema cache** button on the Neon console, then you’re right! Congratulations on gaining this level of understanding 👏 As a reminder, you’ll find this button in the _Postgres database > Data API_ section of the Neon console

**Test your understanding:** Is it possible to go _directly_ to this database/API setup, without going through `anonymous` access? If so, what would the process look like? What SQL statements would you run?

**Check your work:** If all of these scripts ran without errors, you should now see a `user_id` column in the `article` table on the Neon console. The `api` view of that table, `articles`, should also show the column. If you had articles in the database prior to this migration, their `user_id` would say `seed`

### Authentication service on-demand user token setup
The `useAuthService` hook that we have so far is meant to track the sign-up, login, and logout cycle: what happens, how to change things, and when they change. This is overkill for this new category of functionality that just needs to know, at any given time, “who’s on right now?”

This step will do just that. Add the following function to _authService.js_:
```javascript
export const getAccessToken = async () => (await authClient.getSession()).data?.session?.token ?? null
```

That’s it, really—it turns out that the current user’s token can be accessed via the Neon SDK’s `authClient`. It’s a matter of knowing how to get there, and the function above does just that

**Test your understanding:** Is `authClient` doing something that we can otherwise do via native `fetch`? Or does it use a different approach? For once, these are actually sort-of trick questions: at this level, _we don’t have to care_. Abstraction allows us to not sweat the internal details. But if you do want to know how this is done (and if there’s a better way to do it), these are the right questions to ask

**Check your work:** Ye olde `console.log` technique helps us here again: invoke `getAccessToken` at different points in the app’s life cycle to see what it returns. You should see precisely `null` when there is no logged-in user, but an actual value when a user has signed in

### Article service user attribution setup
Now that we know, at any given time, whether a user is logged in and who that is, we can replace the anonymous authentication in _articleService.js_ with actual user data. This is actually a net _reduction_ in code because _authService.js_ now replaces the authentication functionality within _articleService.js_:
1. Delete the `AUTH_URL` constant, the `anonymousToken` variable, and the `extractExpiration` plus `getAnonymousToken` functions from _articleService.js_—_authService.js_ subsumes them all!
2. In their stead, import just `getAccessToken` and revise `dataApiRequest` as follows:
```javascript
// At the beginning of _articleService.js_…
import { getAccessToken } from './authService'

// And `dataApiRequest` now becomes…
async function dataApiRequest(url, { headers, ...options } = {}) {
  if (!DATA_API_URL) {
    throw new Error('VITE_NEON_DATA_API_URL must be set (see .env)')
  }

  const token = await getAccessToken()
  if (!token) {
    throw new Error('Not signed in')
  }

  return checkResponse(await fetch(url, { ...options, headers: { ...headers, Authorization: `Bearer ${token}` } }))
}
```
3. That’s it! _There is no step 3._ Observe how `createArticle` and `fetchArticles` don’t even have to change. Abstraction for the win again!
4. We continue to throw errors for unexpected or undesirable situations: this allows such occurrences to reach React components, where a full range of user interface techniques can be used to report errors in a graceful, friendly, and recoverable manner

**Test your understanding:** Why does this work? What information must the access token have in order to facilitate identifying the user on the database side?

**Check your work:** Log in to your app as different users and create articles as each of them. In the Neon console, the `article` table’s rows should now show different user IDs, each matching their user records in the _Better Auth_ section

### Test suite mock setup
Almost anti-climactically, our last step involves filling one more blank in our test suite: a placeholder for the `getAccessToken` function that we introduced. We return a dummy token here, but may use other values depending on the particular test:
```javascript
vi.mock('../services/authService', () => ({
  useAuthService: vi.fn(),
  getAccessToken: async () => 'test-token'
}))
```

**Test your understanding:** What kinds of tests would require different or more realistic values for `getAccessToken`?

**Check your work:** We don’t need to know how the Neon SDK’s `authClient` keeps track of the current user token, but if it does contact Neon’s servers to do so, this mock will prevent that for sure

> Aaand…exhale 😮‍💨 That’s as far as we’ll go in terms of a walkthrough!

The main purpose in presenting these walkthroughs in distinct sections as opposed to a pre-made sample code repository is to reinforce what you need to _understand_ about how the parts are put together. This understanding is your ultimate takeaway—not specific knowledge about Neon, Postgres, or React. Knowing how database-backed web apps work, _independent_ of the specific technologies involved, is the overall point of this exercise

## Operational Tips/Suggestions
* Note again that the wealth of possibilities means that self-study and experimentation are built into the work involved with this assignment. Make sure to plan accordingly!
* Take advantage of the very distinct layers involved here: the back end (Neon) and the front end (React). To keep the learning manageable, try to look at each layer in isolation—see if you can first get the Neon side to work without any visual interface, possibly just printing things and/or inspecting the console. _Then_ build the user interface on top of it knowing that the back end functionality already works. Or vice versa, if the user interface part looks trickier
* You may make mistakes, change your mind about features, or run into a dead end, all of which will take time—ideally, _build that time in_ when planning out how you will work on the app
* Setup of Prettier has been shown in class, so there is no reason at this point for why your code (all files) wouldn’t be flawlessly formatted, with 100% consistent indentation and spacing, and perfectly consistent blank-line spacing where necessary. Activate “format-on-save” if your editor has it, so you don’t have to ever worry about formatting while working
* Many operational tips and suggestions from the past assignments also still apply—don’t hesitate to review them!

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
