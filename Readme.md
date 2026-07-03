# FreeFire Visits API

A high-performance Python API designed to interact with Garena Free Fire internal servers to fetch, parse, and track player profile visit metrics. This API utilizes serialized Protocol Buffers (Protobuf) to handle data exchange across multiple regional servers.

## Features

* **Protobuf Parsing:** Built-in protocol buffer handlers for lightweight data processing.
* **Multi-Region Support:** Token configuration handlers for regions including Pakistan, India, Bangladesh, and Brazil.
* **Production Ready:** Configured with serverless routing infrastructure optimized for quick deployment.

---

## Project Structure

```text
├── app.py                  # Main API application and routing logic
├── byte.py                 # Byte array utility operations
├── protobuf_parser.py      # Core parser logic translating raw bytes to structured text
├── visit_count_pb2.py      # Compiled Protocol Buffer schema for profile tracking
├── token_pk.json           # Credentials for Pakistan server region
├── token_ind.json          # Credentials for India server region
├── token_bd.json           # Credentials for Bangladesh server region
├── token_br.json           # Credentials for Brazil server region
├── requirements.txt        # Python dependency manifest
└── vercel.json             # Serverless deployment and routing configuration
```

---

## Installation and Setup

### Prerequisites

* Python 3.9 or higher
* pip (Python package installer)

### 1. Environment Configuration

Clone the repository and install the required library components:

```bash
git clone https://github.com
cd FreeFire-Visits-Api
pip install -r requirements.txt
```

### 2. Local Execution

Launch the development web server:

```bash
python app.py
```

The API will bind to your local interface (typically `http://127.0.0`).

---

## API Reference

### Fetch Profile Visit Data

Retrieves processed profile visit metrics for a specified player identifier utilizing dynamic path routing parameters.

* **URL:** `/<region>/<uid>`
* **Method:** `GET`
* **Path Parameters:**
  * `region` (string, required): Supported server regions: `PK`, `IND`, `BD`, `BR`.
  * `uid` (string, required): The target Free Fire Player UID.

#### Sample Request

```bash
curl -X GET "http://127.0.0PK/1901614992"
```

#### Sample Response

```json
{
  "status": "success",
  "uid": "1901614992",
  "region": "PK",
  "visit_count": 4820,
  "timestamp": "2026-07-03T22:35:00Z"
}
```

---

## Cloud Deployment

This repository includes a `vercel.json` specification file, making it ready for serverless runtime architectures. 

To deploy via the Vercel CLI:

1. Install the runtime environment tools: `npm i -g vercel`
2. Initialize deployment: `vercel`

---

## Disclaimer

This project is an independent developer utility designed strictly for educational and analytical purposes. It is not affiliated, authorized, maintained, or endorsed by Garena or any of its affiliates. 

## License

This project is distributed under the MIT License.
