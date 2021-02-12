# Azure Purview Catalog Service REST APIs

This is the Swagger for Azure Purview Catalog Service.

## Dynamic Swagger Web

- Install `python3`
- Download swagger dist zip
```bash
wget https://github.com/swagger-api/swagger-ui/archive/v3.37.0.zip
unzip v3.37.0.zip
cp swagger-ui-3.37.0/dist/* .
```

- Change url in `index.html`
```js
// Begin Swagger UI call region
const ui = SwaggerUIBundle({
url: "data-plane/preview/purviewcatalog.json",
dom_id: '#swagger-ui',
deepLinking: true,
presets: [
    SwaggerUIBundle.presets.apis,
    SwaggerUIStandalonePreset
],
plugins: [
    SwaggerUIBundle.plugins.DownloadUrl
],
layout: "StandaloneLayout"
})
// End Swagger UI call region
```
- host http.server and open in http://localhost:8000
```bash
python3 -m http.server 8000
```

## Static HTML

### Install spectacle
```bash
npm install -g spectacle-docs
```

### Static HTML Generate
```bash
spectacle -D data-plane/preview/purviewcatalog.json -t public
```
A `index.html` will be generated in `public` folder. You can either copy the generated HTML to your web server, or view your docs by pointing your browser to http://localhost:4400/ which can live-reload your change.

## Client SDK
### Install Autorest

> see https://aka.ms/autorest

To build the SDK for Azure Purview Catalog, simply [Install AutoRest](https://aka.ms/autorest/install) and in this folder, run:
```bash
`autorest`
```
To see additional help and options, run:
```bash
`autorest --help`
```
Install `node.js` and `npm`
```bash
`npm install -g autorest@V2`
```

### Client SDK Generate

```bash
autorest --input-file=data-plane/preview/purviewcatalog.json --java --output-folder=PurviewCatalogClient/Java --namespace=PurviewCatalog --add-credentials
```

```bash
autorest --input-file=data-plane/preview/purviewcatalog.json --csharp --output-folder=PurviewCatalogClient/CSharp --namespace=PurviewCatalog --add-credentials
```

Client SDK code will be generated under `PurviewCatalogClient` folder
