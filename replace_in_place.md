# Pull Request example

There is a GitHub repo with a markdown file. This file has some text, a table, and an embedded image.

The goal is to take a screenshot of the table and replace the existing image with the new one.

This example shows a workflow that:

- is triggered when Pull Request is created
- takes a screenshot of a markdown file (from the GitHub web page)
- replaces the existing image
- adds new image as a new commit to the PR
- pushes the changes so they are "visible" in the PR

The workflow is triggered only when a pull request against `screenshot_on_pr` branch is created, so checkout this branch.
This restriction is introcuced, so you have better control over the workflow execution (to make sure no other example workflows fill fire).
You can easily disable it by removing the `branches` section in [the yaml](.github/workflows/replace_img_in_PR.yml).

## How to reproduce

You could copy [the workflow definition](.github/workflows/replace_img_in_PR.yml) to your repo and try it out (please, remember to create `images` directory in this case).

Or, you could clone this repo. Here are the steps if you want to follow the latter approach:

1. Prepare yourself a repository that you could experiment with (where you will be able to create PR, modify workflows, etc.).

   The easiest way is to fork this repository and clone its contents.

   If you are using GitHub CLI, the commands could go like this:

   ```bash
   gh repo fork karol-brejna-i/webpage-screenshot-workflow-examples --clone --org <<your GitHub user>> --remote=true
   cd webpage-screenshot-workflow-examples/
   gh repo set-default <<your GitHub user>>/webpage-screenshot-workflow-examples
   ```

   If you prefer, use the GitHub web interface to fork the repo. (If you do so, please remember to unchecke the "Copy the main branch only" checkbox.)
   Then clone the forked repo and set the default remote to your fork.

2. Make sure actions are enabled in your repo (see: [Troubleshooting](troubleshooting.md#example-workflow-doesnt-start)).

3. It is important, that GitHub workflow is triggered only when a pull request against `screenshot_on_pr` branch is created, so checkout this branch (`git checkout --track origin/screenshot_on_pr`).

4. Create new branch from `screenshot_on_pr` (`git checkout -b some-branch`).

5. Make some modifications to the table in this file.

6. Commit and push the changes (`git add . && git commit -am "Add screenshot" && git push origin some-branch`).

7. Create a pull request against `screenshot_on_pr` branch.
   Use the command line (`gh pr create --base screenshot_on_pr --head some-branch --fill`) or the GitHub web interface.

8. Wait for the workflow to finish.

After successful execution, you should see additional commit and the image added in the PR.

## The table

 **Category**               | **Name**             | **Birthday**                   | **Total Views as of Jan 2023 (approx)**
----------------------------|----------------------|--------------------------------|-----------------------------------------
 Gaming                     | MrBeast Gaming       | 7 May, 1998                    | 5.3 billion
 Gaming                     | PewDiePie            | 24 October 1989                | 28 billion
 Gaming                     | Markiplier           | 28 June, 1989                  | 19.81 billion
 Gaming                     | DanTDM               | November 8, 1991               | 17.1 billion
 Gaming                     | Jacksepticeye        | 7 February, 1990               | 16.02 billion
 Gaming                     | Thinknoodles         | May 30, 1977                   | 8.69 billion
 Gaming                     | Dream                | August 12, 2023                | 2.89 billion
 Gaming                     | Ninja                | June 5, 2023                   | 2.51 billion

## The image

![embedded image](./images/embedded_image.png)
