# Repo Town

Repo Town is a single-file browser experience that turns a GitHub user's public repositories into a soft 2-D village scene.

You enter a GitHub username, the app fetches that user's public repos from the GitHub API, groups them by language, and renders each language as a house in a pastel hillside town. Clicking a house opens an interior view with repo cards, a bookshelf animation, and bird cameos inspired by Mango, Peach, Cherry, Forrest, and Toto.

## What it does

- Fetches public repository data for a GitHub user
- Pulls the user's GitHub profile picture and shows it next to the username
- Groups repos by language and renders the top language groups as houses
- Sorts repos by most recent `updated_at`
- Labels each language area by recency:
  - `active`: updated within the last 90 days
  - `quiet`: 90 days or more
  - `forgotten`: 180 days or more
- Opens a modal "inside the house" view for each language
- Lets you click repo cards to open the GitHub repository in a new tab
- Includes a day/night toggle
- Includes a decorative radio control that tries to find a nearby stream using browser geolocation and Radio Browser

## Project structure

- [index.html](/c:/Users/Dell/Documents/GitHub/RepoTown/index.html): the main app
- [LICENSE](/c:/Users/Dell/Documents/GitHub/RepoTown/LICENSE): license file

At the moment, the project is intentionally lightweight and mostly self-contained inside `index.html`.

## How to run it

Because this is a static HTML app, the simplest option is just to open `index.html` in a browser.

For better browser compatibility, especially for location-based radio:

1. Serve the folder locally with any simple static server.
2. Open `index.html` through `http://localhost/...` or `https`.

Examples:

```powershell
python -m http.server 8000
```

Then visit:

```text
http://localhost:8000
```

## Data sources

Repo Town currently uses:

- GitHub REST API for public user and repository metadata
- Radio Browser API for station lookup
- Browser Geolocation API for approximate user location during radio lookup

## Design notes

- The app is deliberately canvas-driven and playful rather than dashboard-like.
- Language groups become neighborhoods instead of showing one building per repo.
- The town uses soft recency states rather than ranking everything by popularity.
- The birds are part of the world-building:
  - Mango and Peach are the masked lovebird pair
  - Cherry is the Lillian's lovebird
  - Forrest is the colorful red-bellied conure
  - Toto is the dearly loved conure now with another family

## Current limitations

- It currently focuses on public repos unless you extend authentication yourself.
- GitHub OAuth is not fully implemented.
- Radio playback depends on:
  - browser autoplay rules
  - location permission
  - browser support for geolocation
  - whether the returned stream is still healthy
- The app is mostly contained in one large HTML file, which keeps it easy to share but harder to scale.

## Ideas for future improvements

- Split logic into separate JS/CSS files
- Add proper GitHub OAuth
- Add loading skeletons and stronger empty states
- Add branch, topic, and license views
- Add a prettier in-app radio panel
- Add a second visual mode, such as the older low-poly variant

## License

See [LICENSE](/c:/Users/Dell/Documents/GitHub/RepoTown/LICENSE).
