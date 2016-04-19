# DNS Endpoints

This will let you create DNS zones and records for your site. There
is a special NETLIFY record that you can create. This functions
similarly to a CNAME, but it will skip the secondary resolution of
the name. It is a direct link to our internal records.

All DNS record actions are under the domain they're associated with.

## Get all Zones
``` http
GET      /dns_zones HTTP/1.1
```

``` shell
curl \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer {:auth_token}" \
  https://api.netlify.com/api/v1/dns_zones/
```

> Example Response

``` json
[
  {
    "id": "57156bf976f9a7af9ce2b0de",
    "name": "rdn-e2e.com",
    "supported_record_types": [
      "A",
      "MX",
      "CNAME",
      "TXT",
      "NS",
      "SPF",
      "ALIAS",
      "NETLIFY"
    ],
    "user_id": "5715682476f9a7afd1cf4420",
    "created_at": "2016-04-18T23:21:29Z",
    "updated_at": "2016-04-18T23:21:29Z"
  }
]
```

## Creating the Zone
``` http
POST      /dns_zones HTTP/1.1
```

``` shell
curl \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer {:auth_token}" \
  -d '{"user_id": "5715682476f9a7afd1cf4420", "name": "mydomain.com"}' \
  https://api.netlify.com/api/v1/dns_zones
```
> Payload

``` json
{
  "user_id": "5715682476f9a7afd1cf4420",
  "name": "mydomain.com"
}
```

> Example Response

``` json
{
  "id": "571699d476f9a7260e1b935c",
  "name": "mydomain.com",
  "supported_record_types": [
    "A",
    "MX",
    "CNAME",
    "TXT",
    "NS",
    "SPF",
    "ALIAS",
    "NETLIFY"
  ],
  "user_id": "5715682476f9a7afd1cf4420",
  "created_at": "2016-04-19T20:49:24Z",
  "updated_at": "2016-04-19T20:49:24Z"
}
```

## Delete the Zone
``` http
DELETE      /dns_zones/{:id} HTTP/1.1
```
``` shell
curl \
  -X DELETE \
  -H "Authorization: Bearer {:auth_token}" \
  https://api.netlify.com/api/v1/dns_zones/{:id}
```


## Listing all the DNS Records
``` shell
curl
  -H "Authorization: Bearer {:auth_token}" \
  https://api.nelify.com/api/v1/dns_zones/{:zone_id}/dns_records
```

``` json
[
  {
    "id": "5716a12a76f9a72ce9c3b539",
    "hostname": "test.rdn-e2e.com",
    "type": "A",
    "value": "1.2.3.4",
    "ttl": 3600,
    "dns_zone_id": "57169cd776f9a72b479c9977"
  }
]
```

## Creating a DNS Record

``` shell
curl
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer {:auth_token}" \
  -d '{"hostname": "test.mydomain.com", "type": "A", "value": "1.2.3.4" }' \
  https://api.nelify.com/api/v1/dns_zones/{:zone_id}/dns_records
```

> Payload

``` json
{
  "hostname": "test.mydomain.com",
  "type": "A",
  "value": "1.2.3.4"
}
```

> Example Response

``` json
{
  "id": "57169d0576f9a72b479c9978",
  "hostname": "test.rdn-e2e.com",
  "type": "A",
  "value": "1.2.3.4",
  "ttl": 3600,
  "dns_zone_id": "5715682476f9a7afd1cf4420"
}
```

## Creating a linked DNS Record

These records directly creates an link between your site and our traffic director.

Optionally you specify the hostname in the request, otherwise we will
use the custom_domain associated with the site.

This endpoint requires that a site be specified. Its response is the same as
the normal create endpoint.

The payload should be specified with `type` set to "NETLIFY" and the `value` should be the `site_id` of your site.

``` shell
curl
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer {:auth_token}" \
  -d '{"type": "NETLIFY", "value": "{:site_id}" }' \
  https://api.nelify.com/api/v1/dns_zones/{:zone_id}/dns_records
```

## Deleting a DNS Record

``` shell
curl
  -X DELETE \
  -H "Authorization: Bearer {:auth_token}" \
  https://api.nelify.com/api/v1/dns_zones/{:zone_id}/dns_records/{:record_id}
```
