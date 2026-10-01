# NetBird documentation fork

Next.js Pages Router/React/MDX documentation site. Edit authored pages in `src/pages/`, shared presentation in `src/components/`, and MDX processing in `mdx/`. For page authoring, use [MDX conventions](docs/agent-guidance.md#mdx-page-conventions) and [README components](README.md#components-and-use). For page moves, read [navigation](docs/agent-guidance.md#navigation) and [routing](docs/agent-guidance.md#url-routing); for generated API changes, [API generator](docs/agent-guidance.md#api-documentation-generator); for Markdown output, [LLM generation](docs/agent-guidance.md#llm-documentation). Load applicable sections only.

## Authoring boundaries

Page titles come from the first H1; optional descriptions use the existing MDX export convention. Images belong under `public/docs-static/img/<section>/`. Use the existing Note/Warning/Success, layout, and API components rather than introducing parallel conventions.

Update `src/components/NavigationDocs.jsx` when adding or moving pages. Keep the `/api/*` to `/ipa/*` rewrite and legacy redirects in `next.config.mjs` working. Check changed pages, sidebar navigation, and affected redirects in the local browser.

`generator/` owns generated API pages in `src/pages/ipa/resources/`; do not hand-edit that output. `scripts/generate-llm-docs.mjs` produces gitignored `public/llms/`; `dev` and `build` also generate LLM docs and edit routes. Inspect generated changes separately from authored content.

## Verification

From root: `npm install`, `npm run lint`, `npm run build`; `npm run dev` is the local preview. There is no test script in the current package manifest. Match the actual Next.js dependency/runtime requirements rather than the README's older Node 16 note.

`npm run gen` fetches upstream OpenAPI input. Pin/review the intended API version before regeneration; the API workflow has a different pinned-version expansion sequence. Production workflow contains remote SSH deployment and cleanup steps: a successful build is not permission to execute those steps or a deployment claim. Preserve this fork's deployment target and upstream documentation conventions.
