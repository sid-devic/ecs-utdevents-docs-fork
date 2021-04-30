# ecs-utdevents Documentation

Welcome to our documentation site! These docs are to help users, developers, and future maintainers understand how our website works and how you can best take advantage of it.

These docs use [**MkDocs**](https://www.mkdocs.org/).

## Deploying
If you are familiar with Markdown you don't really even need to set up everything below. That's only necessary for local building and testing in case you are adding some new pages/fancy things that you aren't sure will work. Otherwise you can always just edit the files directly on GitHub.

To re-deploy the documents to the GitHub Pages websites, go to the **Actions** Tab in this repository, select **Publish docs via GitHub Pages**, click on **Run Workflow**, select the main branch, and now click on the green **Run Workflow** button.

This will start an automated GitHub Action which will build the main branch and deploy it to our GitHabe Pages website!

## Getting Started
To contribute to and run these docs locally you'll need to download a couple of dependencies.

### Requirements
You'll need Python 3.5+ installed. If you don't have this already then you can downlaod it [here](https://www.python.org/downloads/).

You'll also need pip, a package manager for Python. If you downloaded Python from python.org then you will likely already have it pre-installed. If not you can download it separately [here](https://pip.pypa.io/en/stable/installing/).

To build and test the documents you'll need the following python dependencies:
- mkdocs (1.1.2)
- pymdown-extensions (8.1.1)

Fortunately we've included these dependencies in a `requirements.txt`. So all you have to do is run the following command:

`pip install -r requirements.txt`

### Testing
You can test the docs by navigating into the folder and running the following command:

`mkdocs serve`

This will start a local build at [http://127.0.0.1:8000/](http://127.0.0.1:8000/faq/).

You can find out more detail about local test on [MkDocs website](https://www.mkdocs.org/#getting-started).

