# API to Update IFS Currency Rates
knak.it IFS Currency Rates API is a free service for updating IFS currency rates values [published by the European Central Bank](https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/html/index.en.html).

## Getting Started
You need a API key to use the service. Send an email to [knakit.dev@gmail.com](mailto:knakit.dev@gmail.com?subject=IFS%20Currency%20Rates%20API%20key) with following information.
* Customer ID: Your company name
* Instance ID: IFS Instance (Dev/Test/Prod...etc)
* IFS Url: IFS Instance url with port
* Customer Contact: email for us to update about API changes or downtimes

## Usage
This API is designed to update IFS currency rates from European Central Bank(ECB). You can either create a custom menu to update currency rates whenever required or schedule it to run daily as a IFS scheduled task or Windows task. To use this service, your IFS instance must be open to internet. If your IFS is not open to internet and you are still interested in using this service, please get in touch with [knakit.dev@gmail.com](mailto:knakit.dev@gmail.com).

#### Api Endpoint
```
http://api.knak.it:8290/services/set-ifs-currency-rates
```

#### Sample Body
```xml
<SetIfsCurrencyRatesRequest>
    <ifs:request xmlns:ifs="http://wso2.org/knak/ifs/connector">
            <ifs:CustomerId>DEMOCUST</ifs:CustomerId>
            <ifs:InstanceID>DEMO10</ifs:InstanceID>
            <ifs:apikey>API-KEY</ifs:apikey>
            <ifs:bindVariables>
                <ifs:IfsConnURL>http(s)://DEMOCUST:48080</ifs:IfsConnURL>
                <ifs:IfsVersion>APPS10</ifs:IfsVersion>
                <ifs:IfsCompanyId>1000</ifs:IfsCompanyId>
                <ifs:IfsCurrencyRateType>1</ifs:IfsCurrencyRateType>
                <ifs:IfsRefCurrencyCode>SEK</ifs:IfsRefCurrencyCode>
        </ifs:bindVariables>
    </ifs:request>
</SetIfsCurrencyRatesRequest>
```

#### Authorization
You need to provide IFS username an password as basic authentication header. User ID you provide must be able to insert new records in Accounting Rules > Currency > Currency Rates.

![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) `Please make sure your user ONLY has sufficient access to add curency rates and nothing more`

#### Sample Request
```http
POST /services/set-ifs-currency-rates HTTP/1.1
Host: api.knak.it:8290
Authorization: Basic ZHNtrmRzag==
Content-Type: application/xml
Content-Length: 731

<SetIfsCurrencyRatesRequest>
    <ifs:request xmlns:ifs="http://wso2.org/knak/ifs/connector">
            <ifs:CustomerId>DEMO</ifs:CustomerId>
            <ifs:InstanceID>DEMO10</ifs:InstanceID>
            <ifs:apikey>k73003af-n145-aed6-kae0-ic85401-t412521</ifs:apikey>
            <ifs:bindVariables>
                <ifs:IfsConnURL>https://DEMOCUST:48080</ifs:IfsConnURL>
                <ifs:IfsVersion>APPS10</ifs:IfsVersion>
                <ifs:IfsCompanyId>1000</ifs:IfsCompanyId>
                <ifs:IfsCurrencyRateType>1</ifs:IfsCurrencyRateType>
                <ifs:IfsRefCurrencyCode>SEK</ifs:IfsRefCurrencyCode>
        </ifs:bindVariables>
    </ifs:request>
</SetIfsCurrencyRatesRequest>
```
