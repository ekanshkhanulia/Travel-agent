# AI Travel Agent 🌍✈️

A full-stack AI travel planning app that combines a Gemini-powered chat agent, travel recommendation tools, and a React UI. It collects trip preferences, searches for options, and builds an itinerary while storing conversations and suggestions in SQLite.

## Features

- **Session-based auth**: Sign up, log in, and profile management
- **AI chat**: Google Gemini-powered trip planning flow
- **Flight + hotel search**: Booking.com (RapidAPI) integrations
- **Food + museums**: TripAdvisor integrations
- **Leisure + shops**: Geoapify wiring (currently mocked in agents)
- **Map picker**: Google Maps location selection in the UI
- **Itinerary storage**: Suggestions saved to SQLite and displayed in the UI

## Tech Stack

- **Backend**: Flask, SQLAlchemy, Flask-Session
- **Frontend**: Vite + React + TypeScript + shadcn/ui
- **AI**: Google Gemini (`google-generativeai`)
- **Database**: SQLite (local file)

## Prerequisites

- Python 3.8+
- Node.js 16+
- npm (or yarn)

## Installation & Setup

### Backend

```bash
cd backend
pip install -r requirements.txt
python app.py
```

Backend runs at `http://localhost:5001`.

### Frontend

```bash
cd frontend
npm install
npm run dev
```

Frontend runs at `http://localhost:8080`.

## Environment Variables

Create a `.env` file in `backend/` (or set system env vars):

```
SECRET_KEY=your-secret-key
DATABASE_URL=sqlite:///travel_agent.db
GOOGLE_API_KEY=your_gemini_api_key
BOOKING_API_HOST=booking-com15.p.rapidapi.com
BOOKING_API_KEY=your_rapidapi_key
TRIPADVISOR_API_HOST=tripadvisor16.p.rapidapi.com
TRIPADVISOR_API_KEY=your_rapidapi_key
GEOAPIFY_API_KEY=your_geoapify_key
```

Frontend `.env` in `frontend/`:

```
VITE_GOOGLE_MAPS_API_KEY=your_google_maps_key
```

## Core API Routes (Backend)

- `POST /api/auth/signup`
- `POST /api/auth/login`
- `POST /api/auth/logout`
- `GET /api/auth/user`
- `GET /api/profile`
- `PUT /api/profile`
- `POST /api/conversations`
- `POST /api/travel-chat`
- `GET /api/suggestions/<conversation_id>`
- `POST /api/select_suggestion/<conversation_id>`
- `GET /api/suggestions/<conversation_id>/itinerary-summary`

## Notes / Current Limitations

- Booking actions return recommendations only; users must book externally.
- Geoapify shop/leisure calls are currently mocked in `backend/agents/shop_agent.py` and `backend/agents/leisure_agent.py`.
- Some RapidAPI keys are hardcoded in `backend/agents/booking_client.py` and `backend/agents/flight_client.py`; replace them with environment variables for production use.

---

Happy travels! 🎒✨

