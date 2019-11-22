# Image Transfer Recommendations
When configuring DetectID Digital Onboarding to transfer image files, consider the following:

> **Note**: Bear in mind that the dimensions and quality of the transferred files have an inverse relation with response times. It is necessary to find an adequate balance between image quality and response times, according to the secured entity’s use case

## Identity Validation Processes

| <div style="width:145px">Characteristic</div>  | <div style="width:200px">Recommended Value</div> | Additional Comments |
| -------------- | ----------------- | --------- |
| Optimal dimensions | 820x615p and 1280x960p for PDF417 | none |
| Accepted dimensions | 820x615p to 3120x2340p | none |
| Aspect ratio | 4:3 | none |
| Quality | >=85% | This parameter es very important when it comes to JPEG and other image compression file types. This parameter controls the balance between different characteristics that manage quality and compression. The lower the quality value, the higher the compression will be. The result would be a very compressed image that will be very light and low-quality, possibly, with a large number of artifacts. This is the minimum recommended value |
| Optimal file size | 470kb | none |
| Accepted file size | 470kb - 10MB | none |
| Compression file type | gzip | Onboarding features the possibility of sending the information required for validation in a compressed format to optimize data transference during validation processes. If the information sent in the body of the startup request is compressed, the following string must be added to the header of the request: `"Content-Encoding": "gzip"`  |
