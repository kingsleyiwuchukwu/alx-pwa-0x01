# alx-project-0x14
CineSeek is a modern movie discovery application built with Next.js, TypeScript, and Tailwind CSS. The application allows users to browse movies from the MoviesDatabase API, view movie details, and search for films by year or genre. This project demonstrates how to interact with the MoviesDatabase API (via RapidAPI) using TypeScript. It involves reading API documentation, understanding endpoints, formatting requests and responses, handling authentication, and managing errors.

---

## API Overview

The **MoviesDatabase API** provides extensive information about movies, TV shows, and episodes. It allows users to access detailed metadata, such as title names, release years, ratings, and season/episode information. The API is suitable for applications that require fetching movie-related data like trending titles, upcoming releases, or random selections.

Key Features:
- Retrieve information on movies, TV series, seasons, and episodes.
- Search by ID, title name, or series information.
- Access alternate titles (aka), ratings, and random titles.

---

## Version

**v1 (current)**

---

## Available Endpoints

### Titles

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/titles` | Fetch a list of all titles (movies/shows). |
| GET | `/titles/{id}` | Get detailed information for a specific title. |
| GET | `/titles/series/{seriesId}` | Fetch information about a series using its ID. |
| GET | `/titles/seasons/{seriesId}` | Get all seasons for a given series. |
| GET | `/titles/series/{seriesId}/{season}` | Fetch details of a specific season in a series. |
| GET | `/titles/episode/{id}` | Get episode information by episode ID. |
| GET | `/titles/{id}/ratings` | Fetch user ratings for a specific title. |
| GET | `/titles/{id}/aka` | Retrieve alternate (aka) titles. |
| GET | `/titles/x/upcoming` | List upcoming titles. |
| GET | `/titles/x/titles-by-ids` | Fetch multiple titles using their IDs. |
| GET | `/titles/random` | Retrieve a random title. |

---

## Request and Response Format

### Sample Request using Axios (Node.js)

```ts
const axios = require('axios');

const options = {
  method: 'GET',
  url: 'https://moviesdatabase.p.rapidapi.com/titles',
  headers: {
    'x-rapidapi-key': 'YOUR_API_KEY',
    'x-rapidapi-host': 'moviesdatabase.p.rapidapi.com'
  }
};

async function fetchData() {
  try {
    const response = await axios.request(options);
    console.log(response.data);
  } catch (error) {
    console.error(error);
  }
}
```

### Sample Response

```json
{
  "results": [
    {
      "id": "tt1234567",
      "titleText": {
        "text": "Inception"
      },
      "releaseYear": {
        "year": 2010
      },
      "ratingsSummary": {
        "aggregateRating": 8.8,
        "voteCount": 2000000
      }
    }
  ]
}
```

---

## Authentication

Authentication is required via RapidAPI. Each request must include:

```
x-rapidapi-key: YOUR_API_KEY
x-rapidapi-host: moviesdatabase.p.rapidapi.com
```

- Sign up at [RapidAPI](https://rapidapi.com/) to get your personal API key.
- Do **not** expose your key on the client side.

---

## Error Handling

| Status Code | Meaning | How to Handle |
|-------------|---------|----------------|
| 200 | OK | Success |
| 401 | Unauthorized | Check API key |
| 403 | Forbidden | Key doesn't have permission |
| 404 | Not Found | Check endpoint or ID |
| 429 | Too Many Requests | Wait and retry (rate limit) |

Use `try/catch` blocks in your code to handle errors gracefully. Log or notify errors for debugging and user feedback.

---

## Usage Limits and Best Practices

- RapidAPI rate limits depend on your subscription plan.
- Free tier typically allows ~500 requests/month.
- Avoid unnecessary repeat calls: cache responses when possible.
- Use bulk endpoints (`/titles/x/titles-by-ids`) to reduce total requests.
- Always secure your API key using environment variables or back-end storage.

---

## Author

**Kingsley Iwuchukwu**  
GitHub: [github.com/grafter-ca](https://github.com/kingsleyiwuchukwu)

---

## License

This documentation is prepared as part of the ALX Software Engineering Program and uses data from the MoviesDatabase API (RapidAPI).