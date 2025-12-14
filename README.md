# R-KL Repository Studio

Static Jekyll site that spotlights the public repositories under [R-KL](https://github.com/R-KL).
The homepage reads metadata from `_data/repos.yml` so the GitHub profile can be
shared with a narrative front door.

## Getting started

```bash
bundle install
bundle exec jekyll serve --livereload
```

The site will be available at http://127.0.0.1:4000/Jekyll_Test/ while the server runs.

## Refreshing repository data

1. Use the GitHub API to fetch repository details: https://api.github.com/users/R-KL/repos?per_page=100&sort=updated
2. Update `_data/repos.yml` with the latest metadata (name, description, topics, updated date, stars, forks).
3. Commit the refreshed data so GitHub Pages builds remain deterministic.

## Building for deployment

```bash
bundle exec jekyll build
```

The generated site will be placed in `_site/`. Push the contents of the repository to GitHub
and enable GitHub Pages from the repository settings (use the `main` branch with `/ (root)` as the source).

## GitHub Actions deployment

- The workflow in [.github/workflows/jekyll-pages.yml](.github/workflows/jekyll-pages.yml) builds the site with Jekyll, uploads the `_site` artifact, and deploys it to GitHub Pages.
- After the first push, open **Settings → Pages** and choose **GitHub Actions** as the publish source so deployments follow the workflow.
- Each push to `main` (or a manual **Run workflow**) will rebuild the site using the production configuration and publish the latest `_site` output.

## License

Released under the MIT License. See [LICENSE](LICENSE).
