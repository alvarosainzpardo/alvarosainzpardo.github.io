# Charity Commission API

---

## Como usar el API

La [Charity Commission](https://www.gov.uk/government/organisations/charity-commission) tiene un API SOAP para consultar datos.

En la [homepage del API de la Charity Commission](https://apps.charitycommission.gov.uk/Showcharity/API/APIHome.aspx) hay documentación sobre el API para buscar charities [Search Charities API](https://apps.charitycommission.gov.uk/Showcharity/API/SearchCharitiesV1/Docs/SearchCharitiesV1Home.aspx).

Para poder usar el API, antes hay que [registrarse como usuario desarrollador](https://apps.charitycommission.gov.uk/Showcharity/APIConsole/AccountRegistration/APIConsoleRegister.aspx). Una vez registrado, hay que entrar en la [consola del desarrollador](https://apps.charitycommission.gov.uk/Showcharity/APIConsole/APIConsoleHome.aspx) para crear un proyecto y obtener el API Key necesario para utilizar el API. Se pueden crear varios proyectos para un mismo usuario.

Yo he creado este proyecto:

| Project ID | Project Name | API Key              |
|------------|--------------|----------------------|
| 224        | test1        | dfd1db9b-7a5d-45f8-b |

## Información sobre el API SOAP

En [Developer Guidelines](https://apps.charitycommission.gov.uk/Showcharity/API/SearchCharitiesV1/Docs/DevGuideHome.aspx) hay una tabla con todas las operaciones del API, una breve descripción de cada operación y enlace a la descripción detallada de cada operación.

http://apps.charitycommission.gov.uk/Showcharity/API/SearchCharitiesV1/SearchCharitiesV1.asmx?wsdl es el archivo WSDL del API.

### Descripciones detalladas de las operaciones

#### [GetCharities](https://apps.charitycommission.gov.uk/Showcharity/API/SearchCharitiesV1/Docs/dgGetCharities.aspx)

#### [GetCharitiesByKeyword](https://apps.charitycommission.gov.uk/Showcharity/API/SearchCharitiesV1/Docs/dgGetCharitiesByKeyword.aspx)

#### [GetCharityByRegisteredCharityNumber](https://apps.charitycommission.gov.uk/Showcharity/API/SearchCharitiesV1/Docs/dgGetCharityByRegisteredCharityNumber.aspx)

---

## [charity-commission-api](https://github.com/TimeBandit/charity-commission-api) (paquete Node.js)

This is the *Unofficial* [node package](https://www.npmjs.com/package/charity-commission-api) for the Charity Commission's API. It uses [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) to wrap asynchronous calls around the API.

---

## Savon

Savon is a SOAP client for the Ruby programming language.

* [Source code](https://github.com/savonrb/savon) is hosted on GitHub
* [Releases](http://rubygems.org/gems/savon) are available via RubyGems.org
* Ask questions through the [mailing list](https://groups.google.com/forum/#!forum/savonrb) or on [StackOverflow](http://stackoverflow.com/questions/tagged/savon)
* And receive updates via Twitter

Documentation by version

* [Version 1](http://savonrb.com/version1/) (deprecated)
* [Version 2](http://savonrb.com/version2/) (stable)
* [Version 3](http://savonrb.com/version3/) (unstable)

### Ejemplo de como usar el API de la Charity Commission

```ruby
gem install httpclient
gem install savon

require 'savon'

# create a client for the service
client = Savon.client(wsdl: 'http://apps.charitycommission.gov.uk/Showcharity/API/SearchCharitiesV1/SearchCharitiesV1.asmx?wsdl', convert_request_keys_to: :none)

client.operations
# => [:get_charity_by_registered_charity_number, :get_charity_by_registered_charity_number_and_subsidiary_number, :get_charities, :get_charities_by_keyword, :get_charities_by_name, :get_charity_account_listing, :get_charity_annual_returns, :get_charity_chart_assets_liabilities_and_people, :get_charity_chart_charitable_spending, :get_charity_chart_compliance_history, :get_charity_chart_financial_history, :get_charity_chart_income, :get_charity_chart_spending, :get_charity_chart_income_and_spending, :get_charity_numbers_chart, :get_charity_financial_compliance_table_data, :get_charity_latest_filing, :get_charity_areas_of_operation, :get_charity_published_report, :get_charity_registrations, :get_charity_submissions, :get_charity_subsidiaries, :get_charity_trustees, :get_trustee_and_related_charities]

# call the 'GetCharitiesByKeyword' operation
response = client.call(:get_charities_by_keyword, message: {APIKey: 'dfd1db9b-7a5d-45f8-b', strSearch: 'AgileVentures'})

response.body
# => {:get_charities_by_keyword_response=>{:get_charities_by_keyword_result=>{:charity_list=>{:registered_charity_number=>"1170963", :subsidiary_number=>"0", :charity_name=>"AGILEVENTURES                                                                                                                                         ", :main_charity_name=>"AGILEVENTURES                                                                                                                                         ", :registration_status=>"Registered", :public_email_address=>"info@agileventures.org", :main_phone_number=>"07964143662"}}, :@xmlns=>"http://www.charitycommission.gov.uk/"}}
```

### Enlaces

--- 
