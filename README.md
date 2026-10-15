# VenueVista

VenueVista is a full-stack venue listing and discovery web application inspired by Airbnb-style platforms. It allows users to browse venues, add new venue listings, update existing ones, leave reviews, and manage user accounts through authentication.

The app uses Express.js, MongoDB, EJS templates, Passport.js, Cloudinary, and Mapbox to provide a complete venue marketplace experience.

## Features

- Browse all venues and filter by category or location
- View detailed venue pages with reviews and owner information
- Create, edit, and delete venue listings
- User signup/login/logout using Passport Local authentication
- Flash messages for success and error feedback
- Cloudinary-based image upload for venue photos
- Mapbox geocoding support for location coordinates
- MongoDB-backed data persistence

## Tech Stack

- Node.js
- Express.js
- MongoDB + Mongoose
- EJS templating engine
- Passport.js + Passport-Local-Mongoose
- Cloudinary for image storage
- Mapbox Geocoding API
- Joi for validation
- Express Session + Connect Flash
- Method Override for PUT/DELETE requests

## Project Structure

```text
VenueVista/
├── app.js                  # Application entry point
├── cloudConfig.js          # Cloudinary storage configuration
├── middleware.js           # Auth and validation middleware
├── schema.js               # Joi validation schemas
├── models/                 # Mongoose models
│   ├── listing.js
│   ├── review.js
│   └── user.js
├── routes/                 # Express route definitions
│   ├── listing.js
│   ├── review.js
│   └── user.js
├── controllers/            # Route logic and business logic
│   ├── listing.js
│   ├── review.js
│   └── user.js
├── views/                  # EJS page templates
├── public/                 # Static assets (CSS, JS, images)
├── utils/                  # Utility helpers
├── .env                    # Local environment variables
├── package.json
├── vercel.json             # Deployment configuration for Vercel
└── README.md
```

## How the App Works

1. Users access the homepage, which redirects to `/venues`.
2. The venue listing pages show available venues and allow search/filtering by category or keyword.
3. Authenticated users can create new listings and edit/delete only the listings they own.
4. Venue creation uses Mapbox geocoding to convert the location string into coordinates.
5. Uploaded images are stored in Cloudinary, and the resulting image URLs are saved in MongoDB.
6. Reviews can be added to each listing and are tied to a specific authenticated user.
7. Session management and flash messages keep the user experience smooth and interactive.

## Prerequisites

Before running this project, make sure you have:

- Node.js 20 or later
- MongoDB Atlas account or a local MongoDB instance
- Cloudinary account
- Mapbox access token
- A terminal/command prompt

## Installation

1. Clone the repository:

```bash
git clone https://github.com/Techie-AgrawalJi/VenueVista.git
cd VenueVista
```

2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file in the project root and add the required environment variables:

```env
ATLASDB_URL=mongodb+srv://<username>:<password>@<cluster-url>/<database-name>
SECRET=your_session_secret
MAPBOX_TOKEN=your_mapbox_access_token
CLOUD_NAME=your_cloudinary_cloud_name
CLOUD_API_KEY=your_cloudinary_api_key
CLOUD_API_SECRET=your_cloudinary_api_secret
PORT=3000
NODE_ENV=development
```

4. Start the application:

```bash
npm start
```

5. Open the app in your browser:

```text
http://localhost:3000
```

## Available Scripts

```bash
npm start
```

Runs the server with the main application entry point (`app.js`).

## Environment Notes

- `ATLASDB_URL` is required for MongoDB connection.
- `SECRET` is used for session encryption and authentication.
- `MAPBOX_TOKEN` is used for geocoding venue locations.
- `CLOUD_*` variables are required for uploading images to Cloudinary.
- If you deploy to production, set `NODE_ENV=production` and use a secure session secret.

## Deployment

This project includes a `vercel.json` configuration for deployment on Vercel. Ensure your environment variables are properly configured in the hosting platform before deployment.

## License

This project is licensed under the ISC License.

## Notes

This project is a learning-oriented full-stack application and is structured in a modular way with separate routers, controllers, and models. It reflects a typical Express + MongoDB backend architecture used for venue booking and listing platforms.
