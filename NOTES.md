```
  # ------------------- HDI CONTAINER SERVICE ------------------
  - name: hacap-db
  # ------------------------------------------------------------
    type: com.sap.xs.hdi-container
    parameters:
      service: hana
      service-plan: hdi-shared
      # --- If you can perform the following successfully
      # --- then you don't need the following database_id config
      # cf create-service hana hdi-shared test-hdi
      # --- check with this for "create succeeded"
      # cf service test-hdi | grep status
      # --- Clean up by deleting the service instance
      # cf delete-service test-hdi -f
      # --- otherwise, if you get this error
      # --- Failed to select a database for instance test-hdi, because of: Multiple databases are available
      # uncomment the following lines and specify which one you want
      config:
        database_id: "a992cdc7-4a44-4294-b226-bcdd2df6fbdc"
      # --- Build + Deploy HDI container ONLY
      # mbt build ; cf deploy mta_archives/hacap_0.0.1.mtar
       -r hacap-db
      # --- Clean up with
      # cf undeploy hacap -f --delete-services
    properties:
      hdi-service-name: ${service-name}
```

