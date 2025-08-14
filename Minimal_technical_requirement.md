##### III.2 Minimal technical requirement

This section specifies that you must use a specific set of tools and technologies.
The mandatory requirements also state that no third party libraries or tools are allowed
unless they solve a small, unique task that is part of a larger feature.

- You are free to develop the site, [with or without a backend.](with_without_backend.md)

- If you choose to include a backend, it must be written in pure <a href="Definitions.md#php " title=" general-purpose scripting language geared towards web development">PHP</a>  without <a href="Definitions.md#framework " title=" used by software developers to implement the standard structure of application software">frameworks</a>
. However, this requirement can be overridden by the [Framework
module.](web_modules.md)

- If your backend or framework uses a database, you must follow the constraints
of the  <a href="web_modules.md#minor-module-use-a-database-for-the-backend-and-more." title=" this will take you to databse module">database module</a>. (must use SQLlite)



- The frontend should be developed using Typescript[link to typescript] as base code. However, this
requirement can be modified through the FrontEnd module.[link to front end module]

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

## Modules that help fulfill the requirements
- Minor module: Use a database for the backend: While not mandatory, the requirements imply that you will need a place to store data. A database is the standard way to do this. Alternative storage methods blockchain, in memory stoarge and browser storage. 
- Minor module: Expanding Browser Compatibility: This module helps ensure the game runs on the various browsers that a user might have.


