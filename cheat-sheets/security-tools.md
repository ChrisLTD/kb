# Security Tools

Check your open source dependencies for critical vulnerabilities.

**Yarn**

`$ yarn audit --level critical`

**NPM**

`$ npm audit | grep Critical -B3 -A10`

**Ruby Gems**

`$ gem install bundler-audit`\
`$ bundle audit`

Run all development projects through Docker, a virtual machine, or a remote machine to protect your system and other projects.

### Resources

* [NPM Advisories](https://www.npmjs.com/advisories)
* [NPM Security](https://docs.npmjs.com/auditing-package-dependencies-for-security-vulnerabilities)
* [MacOS security and privacy guide](https://github.com/drduh/macOS-Security-and-Privacy-Guide)
* [Docker for Mac](https://github.com/docker/for-mac)
* [Using Node in Docker](https://www.docker.com/blog/keep-nodejs-rockin-in-docker/)
* [Bundler Audit](https://github.com/rubysec/bundler-audit)
* [OWASP Cheat Sheets](https://cheatsheetseries.owasp.org/)

### Malicious NPM packages

* [https://blog.bitsrc.io/malicious-npm-development-kit-a02401e6537e](https://blog.bitsrc.io/malicious-npm-development-kit-a02401e6537e)
* [https://www.twilio.com/blog/2017/08/find-projects-infected-by-malicious-npm-packages.html](https://www.twilio.com/blog/2017/08/find-projects-infected-by-malicious-npm-packages.html)
* [https://news.ycombinator.com/item?id=17283394](https://news.ycombinator.com/item?id=17283394)
* [https://www.google.com/amp/s/www.zdnet.com/google-amp/article/malicious-npm-packages-caught-installing-remote-access-trojans/](https://www.google.com/amp/s/www.zdnet.com/google-amp/article/malicious-npm-packages-caught-installing-remote-access-trojans/?authuser=0)\
