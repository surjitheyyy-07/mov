# 🎬 CineBook - Scenario 3: Movie Ticket Booking Web Application

An application demonstrating all 4 Experiments of **Scenario 3: Movie Ticket Booking Web Application** using modern React, Redux Toolkit, Axios, REST APIs, and Token-Based Authentication.

---

## 🌟 Interactive Experiments Verification & Implementation Mapping

### 🧪 Experiment 1: Develop Movie Booking Application with API Integration
**Topics:** `REST API`, `Axios`, `Fetch`, `Async Data`
- **a) Fetch movie and theatre information from REST APIs**:
  - Implemented in [`src/store/slices/movieSlice.js`](file:///c:/Users/Admin/Documents/moviebooking/src/store/slices/movieSlice.js) via `fetchMovies` (`GET /api/movies`) and `fetchTheatres` (`GET /api/theatres`).
- **b) Display movies using reusable components**:
  - Created modular [`src/components/MovieCard/MovieCard.jsx`](file:///c:/Users/Admin/Documents/moviebooking/src/components/MovieCard/MovieCard.jsx) with ratings, certificates, badges, duration, and poster artwork.
- **c) Movie search and genre filtering**:
  - Implemented real-time dynamic search and genre chip filters in [`src/pages/Home/Home.jsx`](file:///c:/Users/Admin/Documents/moviebooking/src/pages/Home/Home.jsx).
- **d) Fetch individual movie details dynamically**:
  - Implemented in [`src/pages/MovieDetails/MovieDetails.jsx`](file:///c:/Users/Admin/Documents/moviebooking/src/pages/MovieDetails/MovieDetails.jsx) fetching `/api/movies/:id` dynamically with backdrops, crew, synopsis, and show timings.
- **e) Handle asynchronous API requests using async/await**:
  - Managed with `createAsyncThunk` and `async/await` in Redux slices and Axios instance.
- **f) Display loading and error states**:
  - Created [`src/components/LoadingSpinner/LoadingSpinner.jsx`](file:///c:/Users/Admin/Documents/moviebooking/src/components/LoadingSpinner/LoadingSpinner.jsx) (animated cinema reel) and [`src/components/ErrorMessage/ErrorMessage.jsx`](file:///c:/Users/Admin/Documents/moviebooking/src/components/ErrorMessage/ErrorMessage.jsx) with retry actions.

---

### 🧪 Experiment 2: Implement Movie Booking State Management
**Topics:** `Redux Toolkit`, `Middleware`, `State Architecture`
- **a) Global booking store**:
  - Configured centralized store in [`src/store/store.js`](file:///c:/Users/Admin/Documents/moviebooking/src/store/store.js) combining `authSlice`, `movieSlice`, and `bookingSlice`.
- **b) Manage selected movie, theatre, show timing, and selected seats**:
  - State fields `selectedMovie`, `selectedTheatre`, `selectedShowTime`, `selectedDate`, `selectedSeats` in [`src/store/slices/bookingSlice.js`](file:///c:/Users/Admin/Documents/moviebooking/src/store/slices/bookingSlice.js).
- **c) Actions for selecting and removing seats**:
  - Redux actions `selectSeat` and `removeSeat` handling seat toggling.
- **d) Calculate ticket price and total booking amount**:
  - Tiered seat pricing: Standard (Base), Premium (1.5x), VIP (2x) + Convenience fee computed live with each seat selection.
- **e) Custom Middleware for booking actions**:
  - Implemented in [`src/store/middleware/bookingMiddleware.js`](file:///c:/Users/Admin/Documents/moviebooking/src/store/middleware/bookingMiddleware.js) for seat validation (max 10 seats, unavailable seats prevention) and action logging.
- **f) Maintain booking state across flows**:
  - Persistent state preserved across `MovieList` (`/`) → `MovieDetails` (`/movie/:id`) → `SeatSelection` (`/seats`) → `Checkout` (`/checkout`).

---

### 🧪 Experiment 3: Implement Movie Booking CRUD Operations using APIs
**Topics:** `CRUD`, `REST API`, `Axios/Fetch`
- **a) Retrieve movie and show information using GET**:
  - `GET /api/movies`, `GET /api/theatres`, and `GET /api/bookings?userId=:id`.
- **b) Create a booking using POST**:
  - Executed on checkout submission via `POST /api/bookings` in [`src/pages/Checkout/Checkout.jsx`](file:///c:/Users/Admin/Documents/moviebooking/src/pages/Checkout/Checkout.jsx).
- **c) Modify booking details using PUT/PATCH**:
  - Inline date editing and update via `PUT /api/bookings/:id` in [`src/pages/Bookings/Bookings.jsx`](file:///c:/Users/Admin/Documents/moviebooking/src/pages/Bookings/Bookings.jsx).
- **d) Cancel a booking using DELETE**:
  - Cancellation with confirmation dialog via `DELETE /api/bookings/:id`.
- **e) Display booking history using GET**:
  - Dedicated My Bookings dashboard in [`src/pages/Bookings/Bookings.jsx`](file:///c:/Users/Admin/Documents/moviebooking/src/pages/Bookings/Bookings.jsx).
- **f) Loading and error states for all API operations**:
  - Managed seamlessly with spinners, toasts, and feedback states.

---

### 🧪 Experiment 4: Implement Secure Movie Booking with Authentication and Tokens
**Topics:** `Authentication`, `Token Management`, `Protected APIs`
- **a) User login and sign-up using an authentication API**:
  - Implemented in [`src/pages/Login/Login.jsx`](file:///c:/Users/Admin/Documents/moviebooking/src/pages/Login/Login.jsx) connecting to `POST /api/login` and `POST /api/signup`.
  - Application opens directly to the Login/Sign Up page if not authenticated!
- **b) Store and manage authentication token**:
  - Stored in `localStorage` and managed inside `authSlice`.
- **c) Attach token to booking API requests**:
  - Implemented in [`src/services/api.js`](file:///c:/Users/Admin/Documents/moviebooking/src/services/api.js) via Axios request interceptors attaching `Authorization: Bearer <token>`.
- **d) Protect booking, payment, and booking-history operations**:
  - Client-side route protection using [`src/components/ProtectedRoute/ProtectedRoute.jsx`](file:///c:/Users/Admin/Documents/moviebooking/src/components/ProtectedRoute/ProtectedRoute.jsx) + server-side bearer token validation.
- **e) Logout and token removal**:
  - `logout` action in Navbar flushes `token` and `user` from localStorage and resets state.
- **f) Handle unauthorized and expired-token responses**:
  - Axios response interceptor intercepts 401 statuses, clears token, and redirects to `/login`.

---

## 🚀 How to Run

### 1. Start the REST API Backend Server
```bash
npm run server
```
Runs at: **`http://localhost:3001`**

### 2. Start the Vite React Frontend
```bash
npm run dev
```
Runs at: **`http://localhost:5173`**

### 3. Demo Credentials
- **Email:** `john@example.com`
- **Password:** `password123`
*(Or click "Sign Up" to register any new account)*


---
## Scenario 3 - Experiments 1-3 (Testing, Optimization, Deployment)

- `EXPERIMENTS_GUIDE.md` - commands + where each sub-task (a-f) is implemented
- `DEPLOYMENT.md` - production build, GitHub Pages / Netlify / Vercel steps and comparison

Quick start: `npm install`, then `npm run server` + `npm run dev`, and `npm test` for the Jest suite.
