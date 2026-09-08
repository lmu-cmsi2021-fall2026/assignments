**CMSI 2021** Web Application Development, Fall 2026

# Assignment 0921
We start our practicum with a standalone, single-page web app—one that does not need to communicate with other servers or services in order to do what it seeks to do. In addition, it’s a _bare React_ web app—meaning that we will design and style our app completely _from the ground up_, without any additional frameworks (other than React) nor pre-built style libraries. This deliverable is a means to learning the following:
* An understanding of how web browsers load and start up a web app
* Knowledge of a fair amount of HTML and CSS
* Knowledge of how React improves on pure HTML and CSS by its support for _components_
* Knowledge of basic event handling
* The ability to develop and host an app on [GitHub Pages](https://docs.github.com/en/pages) (thus taking you back full circle to the first item)

It is possible to accomplish everything in this deliverable without gaining the knowledge and understanding described above—if that is what you do, then you have missed the point of the work. Please don’t miss it 🧐

## Background/Preparatory Reading
* Pick and choose among the Tutorials on the [MDN](https://developer.mozilla.org) [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML), [CSS](https://developer.mozilla.org/en-US/docs/Web/HTML), and [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) pages. Bounce around and take in the material you need; you do not have to complete all the tutorials for this assignment. Think of the MDN documentation as something to be read through during the entire course, not just for this assignment (i.e., it can serve both as a _tutorial_ and a _reference_ source)
* Pay particular attention to the MDN CSS tutorials on [flex](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts) and [grid](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Grid_layout/Basic_concepts) layouts. The guides on [CSS-Tricks](https://css-tricks.com) may also include some useful techniques
* Browse the HTML and CSS [HTML Dog tutorials](https://www.htmldog.com/guides/) (3 for HTML and 3 for CSS). You can breeze through them quickly if they cover aspects of these technologies you already know. The goal here is for you to familiarize yourself with all the common uses of HTML and CSS, not to spend too much time. If you find something that interests you, by all means spend as much time as you need
* Review Dr. Toal’s course notes for the introduction to web apps, HTML, CSS, JavaScript. Follow any links in the notes that interest you

Remember that there isn’t enough class time to cover absolutely everything that you might want to do! We hope that our class time so far has served to give you a good foundation for getting started, but definitely don’t let “this wasn’t mentioned in class” be a barrier when it comes to figuring things out

## For Submission
Create a web app that performs a calculation that has the following characteristics:
* It requires at least three user-supplied parameters
* The parameters are of more than one data type
* The calculation/computation produces a definite, verifiable result

All calculations must be functional, robust, and correct. Make the web app as engaging and inviting as possible. Strive to make your users feel like it’s the most effective, enjoyable way to perform that calculation, ever!

Originality of idea is not a priority here, so feel free to use one of these possibilities:
* [Compound interest](https://en.wikipedia.org/wiki/Compound_interest): The core of the page will have a form with input fields for principal, interest rate, number of times compounded per year (_daily_, _weekly_, _monthly_, or _yearly_), and the total number of years. As these values change, the app updates fields showing the amount of money earned and the final total amount
* A sufficiently sophisticated tabletop role-playing game (TTRPG) calculation (saving throw, chance to hit, damage dealt, etc.): The page would include the requisite mix of parameters such as character class, proficiencies, attributes, equipment, and modifiers _plus_ an appropriate die/dice roll. Note that last added aspect, which is unique among the ideas given here. If you go this route, run your specific calculation by the instructor to ensure that it has the requisite sophistication (i.e., it can’t just be “roll a 10 or higher” 😅)
* A _selection_ of compound sports statistics like field goal/free throw percentage, batting average, earned run average, passer rating, etc.: One parameter is the statistic itself, or possibly a choice of sport followed by the available statistics for that sport. Once this is chosen, input fields adjust to the required values, and changes to these values produce the resulting stat
* A _selection_ of unit conversions: One parameter selects the type of unit (e.g., volume, mass, density, speed, etc.), with that selection then determining the available units to/from. When the user enters a value in one unit, the corresponding value in the other unit then appears
* A restaurant bill splitter and tip calculator: Provide a menu of items and prices (feel free to transcribe a real menu from a favorite spot!) then allow the user to specify an order based on those items. Have the user then provide the number of people in the group, the tax rate, and the tip rate, and out pops how much each of them will owe

In addition to the app working correctly, the web app layout must demonstrate these characteristics:
* Responsiveness—the site must look good on mobile and web (narrow or wide screen)
* Site balance and aesthetics—Use colors and contrast properly! Line things up! We aren’t expected to be visual artists, but we can strive to present information in a way that is clear and usable. Optionally, get a designer friend of yours to critique your work

To attain the aforementioned qualities, the following are required—_all_ of them, or no credit will be awarded (as one goal of this assignment is to get you to actually use a large amount of HTML and CSS):

* A background image or gradient
* A grid layout for the main content of the site, so that it has a header and footer
* A flex layout to make the form look gorgeous and responsive
* A nice title (perhaps an `h1` element, with matching CSS)
* A fun image or two (distinct from the background)
* A variety of input elements: don’t just use text! (e.g., sliders, `select`s, checkboxes, radio buttons, etc.)
* Appropriate combinations of margin, padding, and border to make things look clean and polished
* At least one transition
* At least one transform
* At least one text shadow
* At least one box shadow
* At least one link to an external website (like a reference page describing the calculation, or some other primary source)

Follow the instructions below to get your code base set up properly. Test it well

Some additional best-practice requirements:
* Supplement the _README.md_ Markdown file with a description of your app (as real “about” documentation should) alongside the link to where the app is deployed
* Your code (all files) must be flawlessly formatted, and that means that you not only indent and space 100% consistently, but that you are also perfectly consistent with blank-line spacing where necessary. The indentation part is a no-brainer if you follow the setup instructions for Prettier, described below
* The `npm run lint` command will perform a range of automated code-quality checks outside of formatting. Use it frequently and heed its suggestions! (and don’t hesitate to ask if you encounter an error or warning that you don’t understand)
* While working on and testing your app, keep your web browser’s Developer Tools open! Take note of any warnings or errors that appear in the console—there shouldn’t be any except in rare or esoteric edge cases

## Step-by-Step Setup Instructions
Although there are many ways to get yourself set up, this approach helps to standardize things and aligns with what you have seen or will see in class. Many of these steps need to be done only once and will carry over for future projects

### App Boilerplate
The reference for this step is the [Vite Getting Started page](https://vite.dev/guide/). On the command line:
1. Make sure that you have NodeJS installed (`node --version` is an easy way to verify this)
2. Locate yourself (`cd`) to where you’d like your codebase to appear
3. Invoke `npm create vite@latest`
    * Project name: `spa-username` (to align with its GitHub repository)
    * Framework: **React**
    * Variant: **JavaScript + React Compiler**
    * Linter: **ESLint**
    * Install and start now: _Your choice—if you respond “no” then you will see further instructions_
4. General operation: `cd` into the project folder, `npm install` to setup (needed just once), `npm run dev` to launch the web app server, <kbd>control</kbd>-<kbd>c</kbd> to stop the server

**Test your understanding:** What role does Vite play in creating web apps? How is this different from a generative AI prompt for creating one?

**Check your work:** After doing these steps, you should be able to fire up your baseline web app and run it on your web browser of choice

### Editor/Linting/Formatting Setup
These instructions are for VS Code because this is what is used/shown in class. If you prefer a different code editor, these steps should have equivalents that you can perform:
1. Launch the editor
2. Open a new “blank” window
3. Choose _File > Open Folder_ and choose the folder that Vite created in the earlier section
4. If you are asked about “Trust” or “Restricted Mode,” choose _Trust_ (we are going on the assumption that you can trust yourself…right…?)
5. Click the _Extensions_ sidebar icon (as of this writing: fifth from the top, looks like four square boxes)
6. Search for _ESLint_
7. Install the version that is made by _Microsoft_ (i.e., “ESLint”)—more on this as we advance in the class, but may as well have it handy now
8. Search for _Prettier_
9. Install the version that is made by _Prettier_ (i.e., “Prettier - Code formatter”)
10. Display the _Settings_ dialog—there are varying ways to do this: finding it in the menubar may be most convenient
11. Search for “formatter”
12. Set the _Default Formatter_ preference to _Prettier - Code formatter_
13. Search for “format on save”
14. Make sure that the _Format On Save_ preference is checked
15. Create a new file (again, varying ways here so find the one that works best for you)
16. Call it _.prettierrc_ (spell it exactly that way, with the period at the beginning!)
17. Paste the following into it, then save:
```
printWidth: 120
tabWidth: 2
useTabs: false
semi: false
singleQuote: true
quoteProps: 'as-needed'
jsxSingleQuote: false
trailingComma: 'none'
bracketSpacing: true
bracketSameLine: false
arrowParens: 'avoid'
proseWrap: 'preserve'
htmlWhitespaceSensitivity: 'css'
endOfLine: 'lf'
```

Prettier has default settings, but these are the ones I prefer. The main takeaway is this: modern code editors can format our code in a readable and reliable way these days, and the steps above ensure that we all end up with the same formatting conventions

**Test your understanding:** Which of these steps are absolutely necessary? Which are optional or a matter of choice? For this latter, what factors would determine whether or not you would do them?

**Check your work:** After doing these steps, you should be able to edit and customize your baseline web app. In addition, problematic code will be tagged in red (thanks to ESLint) and, whenever you save a file, that file will be formatted in a consistent manner (thanks to Prettier)

_Startup note:_ As generated, Vite’s boilerplate files do _not_ match the above custom formatting rules. But as you work with them (and create your own files), the _Format On Save_ setting will gradually help them converge to the desired style

### GitHub Repository Setup
We will do our work within the GitHub [lmu-cmsi2021-fall2026](https://github.com/lmu-cmsi2021-fall2026) organization. Make sure that you are a member! (if you were not added in class, then contact the instructor)
1. Click on the green _New_ button to create a new repository
2. Name it `spa-username` where _username_ is your GitHub handle
3. These are the defaults, but to be sure, make sure the repository settings say: `Private`, `No template`, _README_ `off`, `No .gitignore`, and `No license`
4. _No_ jumpstart with Copilot either (presumably you know why…)
5. Your repository should initially look _completely_ empty, without even any files. If you see files, delete the repository and start over
6. Instead, you should see different sets of instructions. You want to do something that resembles the _…or create a new repository on the command line_ section, but customized to the fact that you have already created your app boilerplate
7. On your machine’s command line, locate yourself (`cd`) to the folder that Vite created in the first section
8. Use these instructions instead of the ones displayed on the GitHub website (they are _similar_ but not identical—and the second to last command will vary _individually_ because it involves your specific GitHub repository):
```
git init
git add README.md
git add .gitignore .prettierrc README.md eslint.config.js index.html package.json package-lock.json public src vite.config.js
git commit -m "Initial boilerplate."
git branch -M main
git remote add origin git@github.com:lmu-cmsi2021-fall2026/spa-username.git # Needs customization!
git push -u origin main
```

_Note the second-to-last command!_ The last portion depends on your repository name (`spa-username` but with _your_ GitHub username instead of the generic _username_ placeholder) _and_ whether you access your repository via HTTPS or SSH. If you have never done this before, please ask for individual guidance from the instructor

**Test your understanding:** For the commands that are different, why are they different in our case vs. from the GitHub website? What other factors might determine how you set up a GitHub repository for a new project?

**Check your work:** After doing these steps, you should now see your code on the GitHub website. You should now also be able to do the standard `git add`/`git commit`/`git push` cycle to revise your code iteratively and build up your repository’s revision history

### GitHub Pages Setup
At this point, you are now in a position to revise, test, and enhance your web app on your development machine—but it isn’t really a _web app_, isn’t it, until it’s _actually_ on the web 😅 And there are many, many, many, _many_, **many**, _**many**_ ways and variations to do that

To get you started on this long, expansive journey, we have chosen a mechanism that hews closely to the resources that we already have: a GitHub feature called [Pages](https://pages.github.com/). And even this _particular_ feature provides many avenues for getting a web app onto the web. For this assignment, follow [Vite’s own first-party steps for deploying to GitHub Pages](https://vite.dev/guide/static-deploy#github-pages) with these notes:
1. In the first step, we will use the second deployment variant, so set `base` to `/spa-username/` (again, yes, substitute _username_ with your own)
    * At the level of the code, this goes after the `defineConfig` line as `base: '/spa-username/'` (yep you got it, change _username_ accordingly)
    * What the Vite instructions don’t explicitly tell you to do is to `add`, `commit`, and `push` that change to the GitHub server
    * Further, note that after this change, invoking `npm run dev` results in a change to the URL for loading your app
2. Follow the second step as stated, then…
3. …for the third step, choose _create your own_ and copy-paste the given _deploy.yml_ file into the editor that appears. And yes, name that file _deploy.yml_. The file does not need further revision
4. The Vite instructions end there—to round this out, click on _Commit changes…_ and supply a message just as if you invoked `git commit -m "..."` from the command line
5. You modified a file directly on the GitHub server so this file isn’t on your local copy yet. Do a `git pull` in order to bring it in
6. Back on the GitHub site for your repository, click on the _Actions_ tab
7. You should see a workflow run in the list. If it shows a green check icon, then that run has succeeded and you should be ready to go…
8. …to https://lmu-cmsi2021-fall2026.github.io/spa-username/ (change _username_!), and lo and behold, your web app should be up and running there

**Test your understanding:** How does this process align with how a web browser loads and displays a web app? How is it the same as `npm run dev` and how is it different? You can look up the Vite commands `npm run build` and `npm run preview` to broaden your understanding of what’s going on here

**Check your work:** From this point on, committing and pushing to the `main` branch will update the web app at the public URL. You can watch the _Actions_ tab to see the build workflow run (it’s fast but not instantaneous). Once it’s a green check, the URL should now show the latest version of your web app

### Take a Breath
Is that a lot of steps? Yes, yes it is. But the steps were also written in the finest granularity of detail possible to ensure consistent results. In practice, these setup instructions are distilled into single phrases like “initialize your codebase,” “configure your editor,” or “set up your repository.” You want to find yourself at a point where these phrases are all you’ll need, with the specific steps being something you’ve already memorized or can figure out on your own. Ultimately, you won’t even need to be told what these steps should be, because you will know what each step does and you’ll know to do them when you realize that they need to be done

Some of these steps need to be performed just once because they affect how your computer is set up overall. Other steps need to be performed for each project because they affect the project. The takeaway here is that optimal software development requires the right tools and settings. Although you don’t need to memorize them, you should have a general idea of what role each step plays, so that if you encounter something that is inconsistent with what you’re seeing in class, you can track down how to align your setup as needed

## How to Turn it In
* Commit your code to a GitHub repository within the [lmu-cmsi2021-fall2026](https://github.com/lmu-cmsi2021-fall2026) organization with the following naming convention: `spa-username`, where _username_ is your GitHub handle
* Update the _README.md_ file with a description of your app
* Make sure that your deployment is live and functional at https://lmu-cmsi2021-fall2026.github.io/spa-username/ (again with _username_ being your GitHub handle)

## Specific Point Allocations
For this particular assignment, graded categories are as follows:

| Category | Points |
| -------- | -----: |
| Baseline functionality | 40 points total |
| • Ability to enter the necessary parameters, as determined by the intended web app | 15 points |
| • Correct computation of the web app’s target result(s) | 15 points |
| • Effective display of result(s) | 10 points |
| Baseline design/layout | 35 points total |
| • Responsiveness (i.e., the “resize-the-browser-window” test) | 20 points |
| • Site balance and aesthetics | 15 points |
| Implementation specifications | 20 points—all or nothing |
| • Background image or gradient<br/>• Grid layout for the main content<br/>• Flex layout for the form<br/>• Title<br/>• Fun image(s)<br/>• Varied input types<br/>• Margin<br/>• Padding<br/>• Border<br/>• Transition<br/>• Transform<br/>• Text shadow<br/>• Box shadow<br/>• Link to external website<br/>• Functional GitHub Pages deployment | |
| App description in _README.md_ | 5 points total |
| Hard-to-maintain or error-prone code | deduction only |
| Hard-to-read or inadequately-formatted code | deduction only |
| Version control | deduction only |
| Punctuality | deduction only |
| **Total** | **100** |

Note that websites with lingering code errors will negatively affect other criteria, because if we can’t run your code, we can’t evaluate related remaining items completely.
