# Development notes

- Run `docker compose -f docker-compose.base44.yml up -d`; startup runs `npm ci` against the committed lockfile in an isolated dependency volume.
- The app has no database or required credentials. Vault state lives in browser localStorage under `glam_vault_data_v2` and is specific to each browser origin.
- Express serves the bind-mounted `index.html` directly, without a build. Node watch mode reloads server changes; HTML changes require refreshing the preview (there is no browser HMR).
- The affirmation Studio is a remote iframe at `https://glam-weekday-affirmation-studio.netlify.app/`, not source contained in this repository. Its availability and embedding policy are external dependencies. PDF resources and community links also point to external sites.
- Verify startup with `docker compose -f docker-compose.base44.yml ps` and `curl -fsS http://localhost:3000/` (look for `<title>Glam Vault</title>`). The compose healthcheck validates the same page. There is no automated test suite.
