This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app).

## AniList API Routes

This project includes an enhanced Consumet-style AniList API at `src/app/api/meta/anilist/[...route]/route.js`.

### Base URL
```
/api/meta/anilist/{route}
```

### Available Routes

| Route | Method | Description | Query Parameters |
|-------|--------|-------------|------------------|
| `trending` | GET | Get trending anime | `page` (optional) |
| `search` | GET | Search anime by query | `q` (required), `page` (optional) |
| `advanced-search` | GET | Advanced anime search with filters | `search`, `genres`, `format`, `season`, `seasonYear`, `sort`, `adult`, `page` |
| `ongoing` | GET | Get currently airing anime | `page` (optional) |
| `recent` | GET | Get recently updated anime | `page` (optional) |
| `updates` | GET | Get upcoming anime (not yet released) | `page` (optional) |
| `new-releases` | GET | Get new releases | `page` (optional) |
| `completed` | GET | Get completed anime | `page`, `perPage` (optional) |
| `popular` | GET | Get popular anime | `page` (optional) |
| `spotlight` | GET | Get spotlight anime (top 10 trending releases) | - |
| `schedule` | GET | Get anime airing schedule | `page` (optional) |
| `country` | GET | Get anime by country of origin | `country`, `page` (optional) |
| `releasing` | GET | Get currently releasing anime | `page` (optional) |
| `tv` | GET | Get TV format anime | `page` (optional) |
| `movie` | GET | Get movie format anime | `page` (optional) |
| `ona` | GET | Get ONA format anime | `page` (optional) |
| `ova` | GET | Get OVA format anime | `page` (optional) |
| `trending-range` | GET | Get trending anime by time range | `range` (today/week/month) |
| `fetchNameid/{animeName}` | GET | Search anime by name and return best match with ID | - |
| `random-anime` | GET | Get a random anime | - |
| `seasons` | GET | Get all seasons of an anime | `id` (required) |

### Example Requests

```bash
# Get trending anime
GET /api/meta/anilist/trending

# Search for anime
GET /api/meta/anilist/search?q=naruto

# Advanced search
GET /api/meta/anilist/advanced-search?search=action&format=TV&sort=POPULARITY_DESC

# Get anime by ID
GET /api/meta/anilist/fetchNameid/Attack%20on%20Titan

# Get random anime
GET /api/meta/anilist/random-anime

# Get seasons for an anime
GET /api/meta/anilist/seasons?id=16498
```

### Features

- **Rate Limiting**: Built-in rate limiting with 350ms delay between AniList API calls
- **Caching**: In-memory caching with configurable TTL (default: 24 hours)
- **Request Deduplication**: Concurrent identical requests are deduplicated
- **Retry Logic**: Automatic retry with exponential backoff on transient failures
- **CORS Support**: All responses include CORS headers
- **Cache-Control Headers**: Appropriate caching headers for each endpoint

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
