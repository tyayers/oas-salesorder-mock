# SalesOrder API Mock

This provides a mock backend service for SalesOrder data, was well as an Open API 3.1 spec for testing. You can GET and POST data on the /orders endpoint.

# Deployment

To deploy either clone and build the docker image yourself, or just click this button to deploy directly to [Google Cloud Run](https://cloud.google.com/run).

[![Run on Google Cloud](https://deploy.cloud.run/button.svg)](https://deploy.cloud.run)

To run locally using GO:

`go run orderservice.go`

To deploy manually to Google Cloud Run:
```sh
gcloud run deploy oas-order-service --source . --region europe-west4 --allow-unauthenticated
```

To build and run locally using docker:

```
docker build -t local/sap-orders-mock .
docker run -p 8080:8080 local/sap-orders-mock
```

# Test

To test on Cloud Run, call this endpoint:
`curl [YOUR_CLOUDRUN_ENDPOINT]/sap/opu/odata/sap/API_SALES_ORDER_SRV/A_SalesOrder`

To test locally, call this endpoint:
`curl http://localhost:8080/sap/opu/odata/sap/API_SALES_ORDER_SRV/A_SalesOrder`

You should get a lot of SalesOrders returned.  You can also POST new records to the endpoint, which will be persisted in memory until the Cloud Run instance is scaled down.
