# Dcycle Documentation

* [Project home page](https://documentation.dcycle.com).
* [This project on GitHub](https://github.com/dcycle/dcycle-documentation).

## About

Displays a README.md file in a nicely formatted page with a table of contents.

## Quickstart

Copy only the file `index.html` to any GitHub repo which has a README.md file, and enable GitHub Pages.

## Typical usage

* You have a GitHub repo with a README.md file in markdown format
* Add the enclosed index.html file to your GitHub repo
* Enable GitHub pages
* Your README.md file will now displayed in a nicely formatted page
* A table of contents will automatically be generated
* You can change the markup and css of the index.html file to fit your brand

## Example

* The text you are currently reading exists in markdown format on its [GitHub repo](https://github.com/dcycle/dcycle-documentation/blob/main/README.md)
* An [index.html file exists at the same level as the README file](https://github.com/dcycle/dcycle-documentation/blob/master/index.html)
* GitHub Pages is enabled for this repo at `settings:pages`.
* [documentation.dcycle.com](https://documentation.dcycle.com) has a CNAME entry `dcycle.github.io.` (including the trailing dot).
* A [CNAME](https://github.com/dcycle/dcycle-documentation/blob/master/CNAME) file the repo contains `documentation.dcycle.com`.
* Now, <https://documentation.dcycle.com> shows the contents of the README.md file but in a nice format with an automatically-generated table of contents.

## Local development

Most people who modify the README.md file will not need to do anything. This section is for you if you want to see the documentation page locally.

During local development, if you open `index.html` in a browser directly, it might show somethng like:

> Cannot read README.md file from file:// protocol. You might want to try: python3 -m http.server; see https://documentation.dcycle.com for more details.

This is because the Dcycle Documentation index.html file has to read the README.md file and display it; and due to security restrictions, this needs to be done on a webserver.

Here are two quick ways to launch a webserver

### Launch a local server using Python for local development

Run:

    cd /path/to/my/project/
    python3 -m http.server

Then you can visit the site at <http://0.0.0.0:8000>.

### Use Docker with Nginx for local development

If you have Docker installed, you can use the [Nginx image](https://hub.docker.com/_/nginx).

    cd /path/to/my/project/
    docker run -p 1234:80 -v "$(pwd)":/usr/share/nginx/html:ro nginx

Then you can visit the site at <http://0.0.0.0:1234>.

### Use Docker with Apache for local development

If you have Docker installed, you can use the [Apache (httpd) image](https://hub.docker.com/_/httpd).

    cd /path/to/my/project/
    docker run -p 2345:80 -v "$(pwd)":/usr/local/apache2/htdocs/ httpd:2.4

Then you can visit the site at <http://0.0.0.0:2345>.

## Architectural approach

Although several excellent projects exist (see "Other similar projects") to manage documentation, for Dcycle Documentation, our aim is:

* For it to be possible to simply add index.html to any repo which has a README.md file and for the documentation to "just work".
* Extreme simplicity: we don't use a static site generator, everything is done in Javascript directly in `index.html`
* For only one file to be necessary: `index.html`.
* To access external libraries using CDNs to lessen the code in our repo.

## Libraries used

* [jQuery](https://jquery.com) is used to manipulate the DOM.
* [Showdown](https://showdownjs.com) is used to convert markdown to HTML.
* [Bootstrap](https://getbootstrap.com) is used for the visual layout.
* [Tocbot](https://tscanlin.github.io/tocbot/) is used to generate the table of contents.

## Other similar projects

* [Just the Docs](https://just-the-docs.com) is a lot more powerful, with many features.
