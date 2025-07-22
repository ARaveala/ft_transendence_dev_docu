
# Project overview for transcendence.

### Mandatory part
This project is about creating a website for the mighty Pong contest!

Your software will offer a nice user interface and real-time multiplayer capabilities allowing
to play Pong with all your friends!

your project needs to adhere to the mandatory guidelines as a minimum
Some of these constraints may be overridden by the choice of specific
modules.

It is mandatory to do minimum of 7 major modules, 2 minor modules count as 1 major module.
##### III.2 Minimal technical requirement

- You are free to develop the site, [with or without a backend.](with_without_backend.md)

• If you choose to include a backend, it must be written in pure PHP without
frameworks. However, this requirement can be overridden by the Framework
module.
• If your backend or framework uses a database, you must follow the constraints
of the Database module.

- The frontend should be developed using Typescript as base code. However, this
requirement can be modified through the FrontEnd module.

- Your website must be a single-page application. The user should be able to use the
Back and Forward buttons of the browser.

- Your website must be compatible with the latest stable up-to-date version of
Mozilla Firefox . Of course, it can be compatible with other web browsers!

- The user should encounter no unhandled errors or warnings when browsing the
website.
- You must use Docker to run your website. Everything must be launched with a
single command line to run an autonomous container.

Several container technologies exist: Docker, containerd, podman,
etc. On the computers of your campus, you may access the container
software in rootless mode for security reasons. This could lead to
the following extra constraints:
• Your runtime needs to be located in /goinfre or /sgoinfre.
• You are not able to use “bind-mount volumes” between the host
and the container if non-root UIDs are used in the container.
Depending on the current requirements of the subject (highlighted in
green above) and the local configuration in clusters, you may need to
adopt different strategies, such as: container solution in virtual
machine, rebuild your container after your changes, craft your own
image with root as unique UID.

modules
 You will be able to choose the modules you want among a large list, but each module and mandatory element contains technical constraints you cannot bypass. So you can select the topics you like, but not technologies you like.

Some modules may depend on others, some modules may conflict with
others. 
