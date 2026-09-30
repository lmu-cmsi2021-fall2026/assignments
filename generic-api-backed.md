**CMSI 2021** Web Application Development, Fall 2026

# Assignment 1012
This assignment aims to level you up in multiple ways:
* Additional React features and techniques
* Fetching and displaying data from a public API
* Writing asynchronous code in JavaScript
* Optionally, using React Router to simulate multiple “pages”

These features will take us one step closer to the kinds of web apps we encounter everyday 🚀

## Background/Preparatory Reading
* Read whatever [official React documentation](https://react.dev/learn) you might need
* Review Dr. Toal’s course notes on React and web service APIs. Follow any links in the notes that interest you
* Take Eve Porcello’s React Essentials class on [LinkedIn Learning](https://www.linkedin.com/learning/react-js-essential-training-14836121) (access it via [MYLMU](https://my.lmu.edu))
* For even moar learning, go through The Net Ninja’s [Full Modern React Tutorial](https://www.youtube.com/watch?v=j942wKiXFu8&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d)

Optionally, you might also find the following useful:
* [React Router](https://reactrouter.com/home) has its own site—for this course, we’ll be using its [declarative mode](https://reactrouter.com/start/declarative/installation)
* To solidify your Git abilities, read from the beginning through Chapters 3, and Chapters 5 and 6 of the [Git Book](https://git-scm.com/book/en/v2)

## For Submission
Create an interactive React web application that fetches data from an API and displays that data in a way that’s appropriate for the application. Be creative, but also work toward developing an application that would actually be useful. You can use any API that you find: it can be for music, food, restaurants, museums, weather, you name it

Need some API ideas? API lists abound. Try [this one](https://mixedanalytics.com/blog/list-actually-free-open-no-auth-needed-apis/), [this one](https://apilist.fun/), [this one](https://www.postman.com/explore/apis-for-beginners) or (especially) [this one](https://github.com/public-apis/public-apis). Important note: You’ll want to pick APIs that are **_CORS-compatible_**. Stay tuned for when that comes up in class!

First and foremost, you must have a functional and sufficiently bug-free app:
* Effective and/or interesting API use—Don’t just call an API for calling’s sake; envision a potentially useful application for it
* Present the API’s data well—Avoid excessive plain text…structure, stylize, and highlight the information well
* Let your user have a say—Provide at least one use case where the API request is based on user input (e.g., search term? menu choice? settings?)

(if we have enough time or if you can learn it on your own, a web app like this can also benefit from an ability to implement multiple “pages” in your web app, for which you’ll want to aforementioned [React Router](https://reactrouter.com/home) library)

Next, your app should look great outside _and_ inside (i.e., for fellow developers):
* Abstraction of network operations—Declare all network operations as asynchronous functions, with the rest of the code calling those functions. i.e., The only place that `fetch` should be called is within functions that are exported by a pure JavaScript (non-React) module—components should call those functions instead of calling `fetch` on their own. I typically like to call this module _api.js_, but other naming and organizational schemes can work too, as long as they are clear and cleanly abstracted
* Clean `npm run lint` and console log—Watch out for HTML validation and accessibility warnings, or other warnings/errors from React! (_Hint:_ There shouldn’t be any—and if there are, fix them)

In addition to the app working correctly, the web app layout must demonstrate these characteristics:
* Responsiveness—The site must look good on mobile and web (narrow or wide screen)
* Site balance and aesthetics—Use colors and contrast properly! Line things up! We aren’t expected to be visual artists, but we can strive to present information in a way that is clear and usable. Optionally, get a designer friend of yours to critique your work
* Appropriate user interface feedback—The web app should provide visible indicators when it is waiting for asynchronous operations to finish
* Graceful error handling—No unexpected freezes nor stack traces please

As in the first assignment, to attain the aforementioned qualities, we have an all-or-nothing list—_all_ of them, or no credit will be awarded (in order for you to continue to get to know foundational modern HTML and CSS):

* A background image or gradient
* Grid layout for one or more components
* Flex layout for one or more components
* A nice title (perhaps an `h1` element, with matching CSS)
* A fun image or two
* At least one transition

Because apps may vary widely at this point, these CSS properties are not required but keep them in your radar in case your particular app can use them:
* `border`
* `border-radius`
* `box-shadow`
* `margin`
* `padding`
* `position` (particularly `position: absolute` or `position: sticky`)
* `transform`
* `text-shadow`

You’re right, we haven’t seen all of these in class—but they can be looked up!

Set up your repository and deploy your web app in the same way as the first one: follow those same instructions but this time, use the naming convention `generic-api-backed-` prepended to your GitHub username

Finally, revise the boilerplate _README.md_ Markdown file to describe your app. Include a brief description of the API that you have chosen, with a link to its documentation. Highlight anything about the app that you think is particularly interesting or that you’re particularly proud of. Supply the GitHub Pages link of the deployed app

As always, your code (all files) must be flawlessly formatted, and that means that you not only indent and space 100% consistently, but that you are also perfectly consistent with blank-line spacing where necessary. As before, indentation is mostly a no-brainer with Prettier. Effective blank-line choices remain manual and Prettier will respect them. Activate “format-on-save” if your editor has it, so you don’t have to ever worry about formatting while working

## Operational Tips/Suggestions
* Although there is no particular mandated approach toward building API-backed apps, you won’t go wrong with this approach:
    * Start by studying the API. Get to know its features. _Communicate with it directly_ using the [Postman desktop app](https://www.postman.com), _curl_, or similar utilities. Talk to it until you feel that you know it well
    * Make strategic use of temporary `console.log` statements to confirm that information is flowing as expected, before proceeding further with building out user interface elements
* Remember that there isn’t enough class time to cover absolutely everything that you might want to do! We hope that our class time so far has served to give you a good foundation for getting started, but definitely don’t let “this wasn’t mentioned in class” be a barrier when it comes to figuring things out
* Get increasingly better at doing targeted searches on the web. Prepend `MDN` or `react.dev` to scope the search to well-known sources. State the technology (`HTML`, `CSS`, `JavaScript`, `JSX`, `hook`, etc.) to scope things even further. If searching for information on an LLM, state your information need precisely. Keep to instrumental help as much as possible (as described in the syllabus). Resorting the executive LLM use may interfere with your learning
* Note the timing! Now that you have done the first app, you have a clearer idea of how long it takes to put something like this together. _Schedule your work accordingly._ It’s fair to say that for this app, you will take roughly the same amount of time to code up the app itself, but now you also have to factor in:
    1. The time it takes to choose and learn your API
    2. The time it takes to implement network functions
    3. Additional state/logic for showing progress feedback and handling errors

    So make sure to plan accordingly!

## How to Turn it In
* Commit your code to a GitHub repository within the [lmu-cmsi2021-fall2026](https://github.com/lmu-cmsi2021-fall2026) organization with the following naming convention: `generic-api-based-username`, where _username_ is your GitHub handle
* Update the _README.md_ file with a description of your app
* Make sure that your deployment is live and functional at https://lmu-cmsi2021-fall2026.github.io/generic-api-based-username/ (again with _username_ being your GitHub handle)

## Specific Point Allocations
For this particular assignment, graded categories are as follows:

| Category | Points |
| -------- | -----: |
| Baseline functionality | 30 points total |
| • Effective and interesting use of the chosen API | 9 points |
| • Useful or entertaining presentation of data delivered by the API | 8 points |
| • Formation of API requests based on user input | 8 points |
| • Successful deployment to GitHub Pages (particularly, CORS compatibility) | 5 points |
| Baseline code quality | 20 points total |
| This is a composite score indicating how successfully the code has:<br/>• Fully-abstracted API functions<br/>• Warning- and error-free developer console | |
| Design & usability | 30 points total |
| This is a composite score indicating how successfully the app demonstrates:<br/>• Responsive design<br/>• Effective aesthetic choices<br/>• Helpful feedback, especially when waiting for asynchronous operations<br/>• Graceful error handling (e.g., when a network request fails) | |
| Implementation specifications | 15 points—all or nothing |
| • Background image or gradient<br/>• Grid layout<br/>• Flex layout<br/>• Title<br/>• Fun image(s)<br/>• Transition | |
| App description in _README.md_ | 5 points total |
| • App and API description | 2 points |
| • Link to API documentation | 2 points |
| • Link to app deployment | 1 point |
| Hard-to-maintain or error-prone code | deduction only |
| Hard-to-read or inadequately-formatted code | deduction only |
| Version control | deduction only |
| Punctuality | deduction only |
| **Total** | **100** |

Note that websites with lingering code errors will negatively affect other criteria, because if we can’t run your code, we can’t evaluate related remaining items completely
