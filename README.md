# Cryptocurrency Price Tracker

A Node.js backend service that tracks prices of Bitcoin, Ethereum, and Matic, storing historical data and providing statistical analysis.

## Features

- Automated price tracking every 2 hours
- Latest price statistics for each cryptocurrency
- Price standard deviation calculations
- MongoDB storage for historical data
- RESTful API endpoints

## Prerequisites

- Node.js (v14 or higher)
- MongoDB (v4.4 or higher)
- npm or yarn

## Installation

1. Clone the repository:
```bash
git clone https://github.com/YOGANAND2003/Koin_Assignment
cd Backend
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory:
```env
MONGODB_URI=<your-mongodb-url>
PORT=3000
```

4. Start the server:
```bash
node index.js
```

## API Endpoints

### Get Latest Cryptocurrency Stats
```
GET /stats?coin={coinId}
```
- `coinId`: One of `bitcoin`, `ethereum`, or `matic-network`

Example Response:
```json
{
  "price": 40000,
  "marketCap": 800000000,
  "24hChange": 3.4
}
```

### Get Price Standard Deviation
```
GET /deviation?coin={coinId}
```
- `coinId`: One of `bitcoin`, `ethereum`, or `matic-network`

Example Response:
```json
{
  "deviation": 4082.48
}
```

## Background Service

The application runs a background job every 2 hours to fetch the latest cryptocurrency data from CoinGecko API. This data is stored in MongoDB for historical analysis.

## Development

To run the application in development mode with auto-reload:
```bash
npm run dev
```

For production:
```bash
npm start
```

## Project Structure

```
├── Backend/
│   ├── models/
│   │   └── CryptoPrice.js
│   ├── routes/
│   │   └── cryptoRoutes.js
│   ├── services/
│   │   └── cryptoService.js
│── index.js
├── .env
├── package.json
└── README.md
```

## Error Handling

The API includes proper error handling for:
- Invalid cryptocurrency IDs
- Database connection issues
- External API failures
- Missing data scenarios

## Data Sources

This project uses the CoinGecko API v3 for cryptocurrency data. The following endpoints are utilized:
- `/simple/price` - For fetching current prices, market caps, and 24h changes
