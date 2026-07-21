# Myntra Clone — React & Redux Learning Project

A full-stack e-commerce learning project inspired by Myntra. It was developed through guided tutorial-based learning to understand how React, Redux Toolkit, routing, REST APIs and an Express backend work together in a practical application.

[![React](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=white)](https://react.dev/)
[![Redux Toolkit](https://img.shields.io/badge/Redux_Toolkit-1.9-764ABC?logo=redux&logoColor=white)](https://redux-toolkit.js.org/)
[![Node.js](https://img.shields.io/badge/Node.js-Express-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Vite](https://img.shields.io/badge/Vite-4-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)

> **Disclaimer:** This project was created for educational and portfolio purposes. It is not affiliated with, endorsed by or connected to Myntra. Brand names, logos and product images belong to their respective owners.

## Overview

This repository documents the project’s development from a static JavaScript storefront to a component-based React and Redux application connected to an Express API.

It contains three learning stages:

- `1-pre-built-bundle` contains the original static implementation and reference backend.
- `2-actual-backend` contains the Express API used by the React application.
- `3-myntra-react-clone` contains the final React and Redux storefront.

The final React frontend requests product data from the backend, displays reusable product cards, lets users add or remove products from their bag and calculates the order total.

## Learning Objectives

This project was created to practise and understand:

- Breaking a user interface into reusable React components
- Passing data through props and rendering dynamic lists
- Managing shared application state with Redux Toolkit
- Creating Redux slices, actions and reducers
- Configuring client-side routes with React Router
- Fetching asynchronous data from a backend API
- Tracking loading state during API requests
- Building a basic REST API with Node.js and Express
- Reading and writing JSON data on the server
- Calculating shopping-bag totals from application state
- Organising frontend and backend code in one repository
- Using Git and GitHub for version control

## Current Features

- Product catalogue loaded from an Express API
- Responsive product-card layout
- Product ratings, prices and discount information
- Add-to-bag functionality
- Remove-from-bag functionality
- Live bag item counter
- Dedicated shopping-bag page
- Price summary with MRP, discount and convenience fee
- Loading indicator while products are fetched
- Client-side routing with React Router
- Global state management with Redux Toolkit
- Reusable React components
- REST endpoints for reading and adding products
- File-based JSON product storage

## Technology Stack

| Area             | Technologies                       |
| ---------------- | ---------------------------------- |
| Frontend         | React 18, Vite, JavaScript and JSX |
| State management | Redux Toolkit and React Redux      |
| Routing          | React Router DOM                   |
| Styling          | CSS3, Bootstrap 5 and React Icons  |
| Backend          | Node.js and Express.js             |
| Data storage     | JSON file                          |
| Package manager  | npm                                |
| Version control  | Git and GitHub                     |

## Project Structure

```text
Myntra_Clone/
├── 1-pre-built-bundle/
│   ├── node-backend/          # Reference backend
│   └── old-clone/             # Static HTML, CSS and JavaScript version
│
├── 2-actual-backend/
│   ├── data/
│   │   └── items.js           # File-storage helper functions
│   ├── app.js                 # Express server and API routes
│   ├── items.json             # Product data
│   ├── package.json
│   └── package-lock.json
│
├── 3-myntra-react-clone/
│   ├── public/
│   │   └── images/            # Product and logo images
│   │
│   ├── src/
│   │   ├── components/        # Reusable UI components
│   │   ├── routes/            # Application pages and layouts
│   │   ├── store/             # Redux store and slices
│   │   ├── index.css
│   │   └── main.jsx
│   │
│   ├── index.html
│   ├── package.json
│   ├── package-lock.json
│   └── vite.config.js
│
├── .gitignore
└── README.md
```

## Getting Started

### Prerequisites

Install the following before running the project:

- [Node.js](https://nodejs.org/) 18 or newer
- npm, included with Node.js
- Git

Verify the installations:

```bash
node --version
npm --version
git --version
```

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/RAJAT0029/Myntra_Clone.git
cd Myntra_Clone
```

### 2. Start the backend

Move into the backend directory:

```bash
cd 2-actual-backend
```

Install the backend dependencies:

```bash
npm install
```

Start the Express server:

```bash
npm start
```

The API will run at:

```text
http://localhost:8080
```

Keep this terminal running.

### 3. Start the frontend

Open another terminal from the repository root:

```bash
cd 3-myntra-react-clone
npm install
npm run dev
```

Open the address displayed by Vite. It will normally be:

```text
http://localhost:5173
```

> The frontend and backend must run simultaneously for product data to load.

## Available Scripts

### Frontend

Run these commands inside `3-myntra-react-clone`:

| Command           | Purpose                              |
| ----------------- | ------------------------------------ |
| `npm run dev`     | Start the Vite development server    |
| `npm run build`   | Create a production build            |
| `npm run preview` | Preview the production build locally |
| `npm run lint`    | Check the source code with ESLint    |

### Backend

Run this command inside `2-actual-backend`:

| Command     | Purpose                            |
| ----------- | ---------------------------------- |
| `npm start` | Start the Express API on port 8080 |

## API Endpoints

Base URL:

```text
http://localhost:8080
```

| Method | Endpoint     | Description              |
| ------ | ------------ | ------------------------ |
| `GET`  | `/items`     | Return all products      |
| `GET`  | `/items/:id` | Return one product by ID |
| `POST` | `/items`     | Add a new product        |

### Example Product

```json
{
  "image": "images/example.jpg",
  "company": "Example Brand",
  "item_name": "Example Product",
  "original_price": 1999,
  "current_price": 999,
  "discount_percentage": 50,
  "return_period": 14,
  "delivery_date": "25 July 2026",
  "rating": {
    "stars": 4.4,
    "count": 120
  }
}
```

## Application Flow

1. The React application starts.
2. `FetchItems` sends a request to the Express API.
3. The backend reads product information from `items.json`.
4. Product information is returned to the frontend.
5. Redux stores the fetched products.
6. The home page displays the products.
7. Adding a product stores its ID in the bag slice.
8. The bag page matches those IDs with product data.
9. `BagSummary` calculates the final amount.

```text
Express API
     ↓
Fetch request
     ↓
Redux store
     ↓
React components
     ↓
User action
     ↓
Redux update
     ↓
Updated interface
```

## Redux Store

The application uses three Redux slices.

### Items Slice

Stores the product information received from the backend API.

### Bag Slice

Stores the IDs of products added to the shopping bag.

It provides actions for:

- Adding a product
- Removing a product

### Fetch Status Slice

Tracks whether:

- Product loading has started
- Products are currently loading
- Product loading has finished

## What I Learned

Building this project helped me understand the complete data flow of a small full-stack application.

I learned:

- How reusable React components improve code organisation
- How Redux shares state between unrelated components
- How Redux actions update the interface
- How React Router handles navigation without refreshing
- How a frontend communicates with an Express API
- How asynchronous product loading works
- How to calculate shopping-bag totals from state
- How to organise frontend and backend code
- How to manage a project using Git and GitHub

Converting the original static version into React demonstrated how component reuse and centralised state management make applications easier to understand and maintain.

## Planned Improvements

- [ ] Product search
- [ ] Category and brand filters
- [ ] Price and rating filters
- [ ] Product sorting
- [ ] Product-details page
- [ ] Size selection
- [ ] Cart quantity controls
- [ ] Persistent cart using local storage
- [ ] Wishlist functionality
- [ ] User registration and authentication
- [ ] MongoDB database integration
- [ ] Address and checkout flow
- [ ] Order history
- [ ] Better loading and error states
- [ ] Empty-cart and empty-search screens
- [ ] Mobile navigation
- [ ] Fully responsive design
- [ ] Automated frontend and backend tests
- [ ] GitHub Actions workflow
- [ ] Production deployment

## Current Limitations

- The frontend expects the backend to run locally on port `8080`.
- Product information is stored in a JSON file instead of a database.
- Authentication is not implemented.
- Payment processing is not implemented.
- Search and category navigation are currently visual.
- Profile and wishlist controls are currently visual.
- The shopping bag is not retained after refreshing the browser.
- The application currently uses a limited set of sample products.

## Future Architecture

The project can later be reorganised into:

```text
Myntra_Clone/
├── client/
├── server/
├── README.md
├── .env.example
└── .gitignore
```

Future production technologies may include:

- MongoDB
- Secure user authentication
- Environment variables
- API input validation
- Secure CORS configuration
- Automated testing
- CI/CD
- Cloud deployment

## Contributing

Suggestions and contributions are welcome.

1. Fork the repository.
2. Create a feature branch:

```bash
git checkout -b feature/your-feature
```

3. Commit your changes:

```bash
git commit -m "Add your feature"
```

4. Push the branch:

```bash
git push origin feature/your-feature
```

5. Open a pull request.

## Author

Developed by **Rajat** as a React and Redux learning project.

- GitHub: [@RAJAT0029](https://github.com/RAJAT0029)
- Repository: [Myntra_Clone](https://github.com/RAJAT0029/Myntra_Clone)

## Acknowledgements

- Myntra for the visual inspiration
- The React, Redux, Vite and Express communities
- The tutorial resources used during the learning process
- Product images and brand assets belong to their respective owners

## Disclaimer

This application is an independent educational project. It is not an official Myntra application and is not intended for commercial use.

---

If you find this learning project helpful, consider giving the repository a star.
