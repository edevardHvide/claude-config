---
name: reference_pow_predictor_aws
description: Pow Predictor AWS infrastructure — S3 bucket, CloudFront, API Gateway, Lambda proxy IDs
type: reference
---

Pow Predictor (alpine-wind) is deployed to AWS:

- **S3 Bucket:** `pow-predictor-frontend` (eu-north-1)
- **CloudFront:** `E1FX2FUC1H43O2` → `https://d1y1xbjzzgjck0.cloudfront.net`
- **NVE Proxy Lambda:** `pow-predictor-nve-proxy` (eu-north-1)
- **API Gateway:** `1uv0uf8m0g` → `https://1uv0uf8m0g.execute-api.eu-north-1.amazonaws.com`
- **AWS Profile:** `tennis-bot` (same account as Tennis-bot: 605893375372)
- **Deploy skill:** `/deploy` in the alpine-wind project

The NVE proxy exists because `gts.nve.no` doesn't set CORS headers. The Lambda proxies requests and adds `Access-Control-Allow-Origin: *`.
