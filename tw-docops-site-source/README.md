# tw-docops-site

A template for TW DocOps approach

## Prerequisites

- [Docker](https://www.docker.com/products/docker-desktop)

## Getting Started

To create the documentation site:

1. Create your own copy of the repository
2. From your project directory, change directory to `tw-docops-site-source`: `cd tw-docops-site-source`
3. Build the Docker image: `docker build -t tw-mkdocs-img .`
4. To see your documentation site locally, run: `docker run --name {nameofyourcontainer} --rm -it -p 9090:9090 -v ${PWD}:/app tw-mkdocs-img:latest`  
> **Note**: Use the -d flag in the above command to detach your terminal from the running container.
5. Navigate to `http://localhost:9090` to see your changes updating as you work on your docs.
6. When you finish making changes to your docs, stop the container.
  * You can stop the container from the Docker desktop dashboard or using `docker stop {nameofyourcontainer}`

## Building the Static Files

To create the static files needed for the documentation site:

1. From the `tw-docops-site-source` directory, run: `docker run --rm --volume="$PWD:/app" -it tw-mkdocs-img:latest mkdocs build && (cd .. && cp -r tw-docops-site-source/site docs)`  
  This command builds the static files into a directory called `site` and then copies the static files and places them into a directory called `docs` in the root directory so that GitHub Pages can take the static files from there.
2. Commit and push your changes to your GitHub repository.
3. Navigate to your GitHub repository
4. Go to the **Settings** tab
5. Navigate to the **GitHub Pages** section
6. In **Source**, select `Branch: main` and `/docs` as the source for GitHub Pages
7. Click **Save**
8. Navigate to your site, it should be something like: `https://{yourGitHubUserName}.github.io/tw-docops-site/`

