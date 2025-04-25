# 📦 Html Label PDF Generator

> A Spring Boot service that accepts a POST request with shipping data in JSON format, fills a label HTML template with barcodes, and returns a generated PDF.

---

## Workflow
<img width="400" alt="image" src="https://github.com/user-attachments/assets/7c098946-5353-4099-b8fd-c4df86367b95" />


## ✨ Features

- ✅ REST API to receive label information via JSON
- ✅ HTML label template rendering
- ✅ Barcode generation using ZXing
- ✅ HTML to PDF rendering using OpenHTML to PDF

---

## 📂 Project Structure

```
fbm-wms-printing-service/
├── printing-html-label-api/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/maersk/fbm/printing/html/label/
│   │   │   │       ├── controller/           # HtmlLabelController
│   │   │   │       ├── dto/                  # HtmlLabelDto
│   │   │   │       ├── service/              # HtmlLabelService & Impl
│   │   │   │       ├── util/                 # BarcodeUtil
│   │   │   │       └── HtmlLabelApplication  # Spring Boot Application
│   │   │   └── resources/
│   │   │       ├── shipping-label-template-0.html
│   │   │       ├── shipping-label-template-1.html
│   │   │       └── shipping-label-template-2.html
│   ├── test/
│   └── pom.xml
├── printing-service-common/                
├── pom.xml
```

---

## 🧰 Technology Stack

- Java 17
- Spring Boot
- ZXing (Barcode)
- OpenHTML to PDF

---

## 📬 API Overview

| Method | Endpoint              |Content-Type|Accept| Description                      |
|--------|-----------------------|------------|------|----------------------------------|
| POST   | `/api/html-label` |`application/json`|`application/pdf`| Generates a PDF label from JSON |


#### Example JSON Body:

```json
{
  "templateType": "1",
  "from": "BIG SUPPLIER 5th AVENUE NEW YORK USA",
  "to": "GREAT VALUE 8163 NEW CAJUN DAYTON, OHIO USA",
  "shiptopost": "(420)45458",
  "carrier": "Best Freight",
  "bl": "853903",
  "pro": "2895769860",
  "shipToPostBarcodeText": "(420)45458",
  "ssccBarcodeText": "(00)006141411234567890"
}
```

#### Response:

- Returns a PDF file (`Content-Type: application/pdf`)
- Contains the shipping label filled with provided data and barcodes

<img width="990" alt="image" src="https://github.com/user-attachments/assets/86f4d5d0-80b6-4348-bd5c-8a9bace3a639" />


---

## 🧾 HTML Template

Path: `src/main/resources/

```html
<div class="address">
    {{from}}
</div>
<div class="sscc-code">
    <img src="{{ssccBarcode}}"></img>
</div>
```

---

## 🖨️ Barcode Generation

This service uses ZXing to generate Code 128 barcodes and embed them into the HTML as base64 PNG images.

---




## 🙌 Acknowledgments

- [ZXing](https://github.com/zxing/zxing) - Barcode generation
- [Open Html to PDF](https://github.com/danfickle/openhtmltopdf) - PDF rendering

---

