
# Project overview for transcendence.

### Mandatory part
"This project is about creating a website for the mighty Pong contest!. 

Your software will offer a nice user interface and real-time multiplayer capabilities allowing
to play Pong with all your friends!"

The core of the project is to build an online multiplayer Pong game.
The final product should be a full stack web application with user accounts and a playable game.

your project needs to adhere to the mandatory guidelines as a minimum
Some of these constraints may be overridden by the choice of specific
modules.

It is mandatory to do minimum of 7 major modules, 2 minor modules count as 1 major module.


#### Modules that help fulfill the requirements
- Minor module: Support on all devices: The overview specifies "web application," potentially implying it should be accessible on various devices. This module directly addresses that.

- Major module: Standard user management...: The brief mentions a user management system is necessary for the game (with user accounts). This module provides a complete solution for that.


##### III.2 Minimal technical requirement

- You are free to develop the site, [with or without a backend.](with_without_backend.md)

- If you choose to include a backend, it must be written in pure PHP without
frameworks. However, this requirement can be overridden by the Framework
module.
- If your backend or framework uses a database, you must follow the constraints
of the Database module. (must use SQLlite)

- The frontend should be developed using Typescript as base code. However, this
requirement can be modified through the FrontEnd module.

- Your website must be a [single page](https://en.wikipedia.org/wiki/Single-page_application) application. The user should be able to use the Back and Forward buttons of the browser.

- Your website must be compatible with the latest stable up-to-date version of
Mozilla Firefox . Of course, it can be compatible with other web browsers!

- The user should encounter no unhandled errors or warnings when browsing the
website. **add a list of typical errors, include typical oversights**

- You must use Docker to run your website. Everything must be launched with a
single command line to run an autonomous container.this means :
- You can run scripts directly on the host system but The app runs entirely inside the container, with no need for extra setup on the host
- Your entire stack (frontend, backend, assets, database, etc.) lives inside the container

On the computers of your campus, you may access the [container
software in rootless mode](choosing_rootles.md) for security reasons.

• Your runtime needs to be located in /goinfre or /sgoinfre.

// this should be removed , check if any useful data there first We are not restricted to using Docker, [here](container_technologies.md) is a small rundown of choices

 You will be able to choose the modules you want among a large list, but each module and mandatory element contains technical constraints you cannot bypass. So you can select the topics you like, ***but not technologies you like***.

# ‼️  IMPORTANT TO REMEMBER ‼️ 
- The use of libraries or tools that provide an immediate
and complete solution for an entire feature or module is
prohibited.
- Any direct instruction regarding the use (can, must, can’t) of
a third-party library or tool must be followed.
- The use of a small library or tool that solves a simple,
unique task, representing a subcomponent of a larger feature
or module, is allowed.
- During the evaluation, the team will justify any use of a
library or tool that is not explicitly approved by the project
guidelines and is not in contradiction with the project’s
constraints.
- During the evaluation, the evaluator will determine whether the
use of a specific library or tool is legitimate (and allowed)
or if it essentially solves an entire feature or module (and is
therefore prohibited).
 

Some modules may depend on others, some modules may conflict with
others. **add a table of modules that conflict with eachother**
