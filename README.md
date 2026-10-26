# Mortgage Comparison Auditor

A small Express app for entering mortgage offers from different lenders and comparing their monthly payment and total cost. It is for home buyers weighing a few loan quotes side by side.

## Features

- Record an offer with lender, principal, rate, term in years, and fees
- Calculates the monthly payment using the standard amortization formula
- Calculates the total paid over the life of the loan
- Lists offers sorted by total cost
- Saves offers to a local `data.json` file

## Getting started

Requires Node.js.

```bash
npm install
npm start
```

The server runs on http://localhost:3018. Add an offer and list them:

```bash
curl -X POST http://localhost:3018/api/loans \
  -H "Content-Type: application/json" \
  -d '{"lender":"First Bank","principal":400000,"rate":6,"term":30,"fee":2500}'

curl http://localhost:3018/api/loans
```

## How it works

- `server.js` is an Express server with `POST /api/loans` and `GET /api/loans`. POST returns the calculated loan.
- The payment calculation currently rounds the rate down to a whole number (6.5 is treated as 6), and fees are stored but not added to the total cost.
- Offers are stored in `data.json` in the project folder, which is created on first run and ignored by git.
- `index.html` is served at the root URL but is still a generic placeholder form that is not connected to this API. `utils.js` contains helpers that `server.js` does not use yet.

## Status

Prototype. Rate quotes are entered by hand; the web page is not wired up, and there is no validation or authentication.

## License

MIT, see [LICENSE](LICENSE).
