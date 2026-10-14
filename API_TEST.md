# API Test

The backend described in the training script exposes:

- `GET /health`
- `POST /predict`

## Health check

```bash
curl http://127.0.0.1:5000/health
```

## Prediction request

The model expects 24 hourly observations with 20 features each.

Example JSON structure:

```json
{
  "input": [
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
  ]
}
```

The `input` array must contain exactly 24 rows, with 20 values in each row.

Do not use the all-zero example as a meaningful prediction input; replace it with properly prepared feature values.
