# Alai Challenge - Presentation from Webpage

The goal of the challenge is to write a script that takes in any arbitrary webpage as a URL and output a sharable link to an Alai presentation made from the content of the webpage.
As

## Notes

1. Web Scraping: Use Firecrawl API (https://www.firecrawl.dev/) to scrape the input webpage. Sign up for a free API key.

2. Presentation Creation: Create a 2-5 slide presentation using Alai endpoints. Since Alai's API is undocumented, you'll need to:

   - Create an account at www.getalai.com
   - Use Chrome's network tab to identify the required API endpoints
   - Chain these endpoints to create the presentation automatically

3. Authentication: Alai endpoints require an access token that expires every 30 mins - 2 hours. You'll need to refresh this token periodically.

4. Final Output: Your script should output a shareable Alai presentation link (Example: https://app.getalai.com/view/9W1ic45gS1Kc3iSWv4N42A)

5. Documentation: Create a 1-2 minute Loom video explaining your solution and approach.

6. Extra Credit: Improve presentation quality through:

   - Better slide creation instructions / use of scraped content etc
   - Image imports from webpages
   - Other creative improvements

7. For any questions, reach out at anmol@getalai.com

Document any extra credit work in your Loom video.






# Alai Webpage Converter

A TypeScript/Express service that converts webpages into Alai presentations.

## Features

- Takes any URL and converts it into an Alai presentation
- Extracts key content, headings, paragraphs, and images
- Creates a well-structured 2-5 slide presentation
- Returns a shareable Alai presentation link

## Project Structure

```
alai-webpage-converter/
├── src/
│   ├── config/           # Configuration settings
│   ├── controllers/      # Request handlers
│   ├── middleware/       # Express middleware
│   ├── routes/           # API routes
│   ├── services/         # Business logic
│   ├── types/            # TypeScript type definitions
│   ├── utils/            # Utility functions
│   └── server.ts         # Application entry point
├── .env                  # Environment variables (gitignored)
├── .env.template         # Template for environment variables
├── package.json          # Project dependencies
├── tsconfig.json         # TypeScript configuration
└── README.md             # Project documentation
```

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- Firecrawl API key (sign up at https://www.firecrawl.dev/)
- Alai account (sign up at https://www.getalai.com/)

### Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd alai-webpage-converter
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file from the template:
```bash
cp .env.template .env
```

4. Add your API credentials to the `.env` file:
```
PORT=3000
FIRECRAWL_API_KEY=your_firecrawl_api_key
ALAI_EMAIL=your_alai_email@example.com
ALAI_PASSWORD=your_alai_password
```

5. Build the TypeScript code:
```bash
npm run build
```

6. Start the server:
```bash
npm start
```

For development with hot-reloading:
```bash
npm run dev
```

## API Reference

### POST /api/convert

Converts a webpage into an Alai presentation.

**Request Body:**
```json
{
  "url": "https://example.com/webpage-to-convert"
}
```

**Success Response:**
```json
{
  "success": true,
  "data": {
    "presentationUrl": "https://app.getalai.com/view/presentationId"
  }
}
```

**Error Response:**
```json
{
  "success": false,
  "error": "Error message"
}
```

### GET /api/health

Health check endpoint.

**Response:**
```json
{
  "status": "ok",
  "timestamp": "2025-04-07T12:00:00.000Z"
}
```

## How It Works

1. The API receives a URL to convert
2. It scrapes the webpage content using Firecrawl API
3. The content is processed to extract key information
4. A presentation structure is created with appropriate slides
5. The presentation is created in Alai through their API
6. A shareable link is generated and returned

## License

This project is licensed under the MIT License - see the LICENSE file for details.
