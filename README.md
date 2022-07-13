# AlayaMarket External Documentation

The AlayaMarket external API documentation will be made publicly available here. 
The API specifications are maintained elsewhere and should be synchronized with this repository. 
This will be done manually for now, but should be replaced by an automated flow. 

## Architecture 

The project is using GitHub pages to host documents. 

This is based on the template 
[github.com/peter-evans/swagger-github-pages](https://github.com/peter-evans/swagger-github-pages)
(workflow to update Swagger UI has been removed).


The OpenAPI and AsyncAPI specifications are copied here from [github.com/AlayaCare/alayamarket](https://github.com/AlayaCare/alayamarket).  
This is currently done manually, but should be replaced by a GitHub action to keep these files in sync. 

### OpenAPI
OpenAPI specs are displayed using [Swagger UI](https://swagger.io/docs/open-source-tools/swagger-ui/usage/installation/). 


### AsyncAPI 
AsyncAPI specs are displayed by generating html using [AsyncAPI Generator](https://www.asyncapi.com/tools/generator):
```shell
npm install -g @asyncapi/generator
ag docs/offers/asyncapi.external.offers.yaml @asyncapi/html-template -o docs/offers/asyncapi.external.offers
```

## Documentation 

A user guide is available [here](https://alayacare.github.io/alayamarket-external-docs/docs/user_guide/). 

The complete list of documentation can be accessed from 
[alayacare.github.io/alayamarket-external-docs](https://alayacare.github.io/alayamarket-external-docs/)

## Next Steps

* Automatically generate new pull requests to update documents when they change 
* Consider automatically updating SwaggerUI dependency as done in the original 
[template](https://github.com/peter-evans/swagger-github-pages)
* Investigate using [Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll)
