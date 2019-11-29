# Temporary
   1. test
   1. test
   ```c
   ESP_LOGI(TAG, "[APP] Free memory: %d bytes", esp_get_free_heap_size());

   esp_err_t ret;

   const char *filename = "/spiffs/SCSH_COOKE_20190826.wmfw";

   // Use settings defined above to initialize and mount SPIFFS filesystem.
   ctc_spiffs_init();
   // Choose which ADSP2 core to download to
   selectCore();

   // WMFW file
   ret = (esp_err_t)ProcessWMFWFile(filename);
   if (ret != ESP_OK) {
      ESP_LOGE(TAG, "[ 0 ] process wmfw file error : %d", ret);
   }
   else {
      ESP_LOGE(TAG, "[ 0 ] process wmfw file success");
   }

   ```
