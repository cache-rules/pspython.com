# Setup

1. Clone this repo somewhere on your machine.
2. Install Python
3. [Install Lektor](https://www.getlektor.com/docs/installation/)
    - Lektor requires imagemagick which can be installed via `brew install imagemagick` on OS X.
4. To run the dev server run `lektor serve`, which will start a web server at
`http://127.0.0.1:5000/` where you can preview the site, and access the admin panel.

# Adding content

Adding content in Lektor is pretty easy, just go to the localhost server and use the UI to add a new
page.

Adding content manually is also pretty straightforward, for the most part you need to do two things:
* Create a folder somewhere in the `/content` folder, where the name of the folder will be the
desired URL slug (for example `content/hello-world/` will become `www.pspython.com/hello-word/`).
* Create a `contents.lr` file in the folder you just created, this will host all of the text content
and other settings for the page. A `contents.lr` file is is a key-value file, where each key and
value is separated by `---`, which allows values to be multiline.
* If you want to use a UI to do this work for you, you can start the dev server and navigate to the
admin panel [http://localhost:5000/admin/root/edit](http://localhost:5000/admin/root/edit)
* For additional info see the [Lektor Content Docs](https://www.getlektor.com/docs/content/)

## Adding a link to the index
1. Determine what icon you want to use for the link
2. Open databages/home_links.json
3. Add an object that specifies the href, icon, and title
4. Add the key to that object in the "links" array

## Adding a member to the CoC Comittee
1. Open coc_staff.json
2. Add the new staff member

## Adding a page manually
1. Create a new folder in `content/`, where the folder name is the desired URL of your post
(for example `content/hello-world` will become `www.pspython.com/hello-world`)
2. Add a `contents.lr` file with the following contents:
    ```
    _model: page
    ---
    title: Your Title Here (Can be different than folder name)
    ---
    body:
    # The Contents of the page
    All of this supports [Markdown](https://www.markdownguide.org/basic-syntax)
    ```

# Deploying

Deploying is easy:

First you must build:

```
$ lektor build
```

Then deploy:

```
$ lektor deploy ghpages
```
Lektor will commit the built site to the `gh-pages` branch, and push, which will get deployed by
GitHub automatically.
