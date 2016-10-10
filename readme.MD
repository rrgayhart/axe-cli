# axe-cli

Provides a command line interface for aXe to run quick accessibility tests.

## Getting Started

Install [Node.js](https://docs.npmjs.com/getting-started/installing-node) if you haven't already.

Install axe-cli globally: `npm install axe-cli -g`

Lastly, install the webdrivers of the browsers you wish to use. A webdriver is a driver for your web browsers. It allows other programs on your machine to open a browser and operate it. Current information about available webdrivers can be found at [selenium-webdriver project](https://www.npmjs.com/package/selenium-webdriver). Alternatively, you could use [Webdriver manager](https://www.npmjs.com/package/webdriver-manager)

## Usage

After installing, you can now run the `axe` command in your CLI, followed by the URL of the page you wish to test:

	axe https://www.deque.com

You can run multiple pages at once, simply add more URLs to the command. If you do not specify the protocol, http will be used by default

	axe www.deque.com, dequeuniversity.com

## Running specific rules

You can use the `--rules` flag to set which rules you wish to run, or you can use the `--tags` to tell axe to run all rules that have that specific tag. For example:

	axe www.deque.com --rules color-contrast,html-lang

Or, to run all wcag2a rules:

	axe www.deque.com --tags wcag2a


A list of rules and what tags they have is available at: https://dequeuniversity.com/rules/worldspace/2.0/.

### Saving the results

Results can be saved as JSON data, using the `--save` and `--dirname` flags. By passing a filename to `--save` you indicate how the file should be called. If no filename is passed, a default will be used. For example:

	axe www.deque.com --save deque-site.json

Or:

	axe www.deque.com --dirname ./axe-results/

### Defining the scope of a test

If you want to only test a specific area of a page, or wish to exclude some part of a page you can do so using the `--include` and `--exclude` flags and pass it a CSS seletor:

	axe www.deque.com --include #main --exclude #aside

### Custom axe-core versions

Axe-cli will look for locally available versions of axe-core. If the directory from where you start axe-cli has an `axe.js` file, or has a `node_modules` directory with axe-core installed in it. Axe-cli will use this version of axe-core instead of the default version installed globally.