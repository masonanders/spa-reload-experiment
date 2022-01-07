# File-Based New-Version Detection Experiment

This is a proof-of-concept on a system to prompt users to reload the client when a new version is detected. This is especially important with single-page applications where changes may be deployed but will not be reflected on the client instance until the page has been reloaded. The idea is that we serve a file containing the version identification, ideally created autonomously at build-time, and periodically poll the server (bypassing the browser's cached version of that file) for that file. If the file's contents change, an element will be rendered prompting the user to reload the page so that any other changes to the application implementation may be reflected on the client instance.

**Example**

The `.gif` below shows the main page in the moments before a change to the `version.txt` finishes deploying. Once the deploy has completed, a `fetch` call for `version.txt` is eventaully made and it's contents are found to be different from it's state when the page was first loaded. The UI then promps a page reload which causes the main page to reflect the new version.

<kbd>
  <img src="https://user-images.githubusercontent.com/37194330/148475176-5372bc80-eb81-4384-9d61-50b1e6b29ecd.gif" />
</kbd>
