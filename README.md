# PYTHON-AMAZON-SP-API


## Amazon Selling-Partner API

A wrapper to access **Amazon's Selling Partner API** with an easy-to-use interface.


### Version 1 Upgrade notice

Version 1 removes AWS IAM or AWS Signature Version 4 authentication.
You can now use the library without AWS credentials.
For compatibility reasons, you can still pass AWS credentials, but they are silently ignored.

### Q & A

If you have questions, please ask them in GitHub discussions 

[![discussions](https://img.shields.io/badge/github-discussions-brightgreen?style=for-the-badge&logo=github)](https://github.com/saleweaver/python-amazon-sp-api/discussions)

or

[![join on slack](https://img.shields.io/badge/slack-join%20on%20slack-orange?style=for-the-badge&logo=slack)](https://join.slack.com/t/sellingpartnerapi/shared_invite/zt-zovn6tch-810j9dBPQtJsvw7lEXSuaQ)

---

### Donate


[:heart: Donate](https://github.com/sponsors/saleweaver)


### Installation
[![Badge](https://img.shields.io/pypi/v/python-amazon-sp-api?style=for-the-badge)](https://pypi.org/project/python-amazon-sp-api/)
```
pip install python-amazon-sp-api
```

---
### Usage

```python
from sp_api.api import Orders
from sp_api.api import Reports
from sp_api.api import Feeds
from sp_api.base import SellingApiException
from sp_api.base.reportTypes import ReportType
from datetime import datetime, timedelta

# orders API
try:
    res = Orders().get_orders(CreatedAfter=(datetime.utcnow() - timedelta(days=7)).isoformat())
    print(res.payload)  # json data
except SellingApiException as ex:
    print(ex)


# report request     
createReportResponse = Reports().create_report(reportType=ReportType.GET_MERCHANT_LISTINGS_ALL_DATA)

# submit feed
# feeds can be submitted like explained in Amazon's docs, or simply by calling submit_feed

Feeds().submit_feed(<feed_type>, <file_or_bytes_io>, content_type='text/tsv', **kwargs)

# PII Data

Orders(restricted_data_token='<token>').get_orders(CreatedAfter=(datetime.utcnow() - timedelta(days=7)).isoformat())

# or use the shortcut
orders = Orders().get_orders(
    RestrictedResources=['buyerInfo', 'shippingAddress'],
    LastUpdatedAfter=(datetime.utcnow() - timedelta(days=1)).isoformat()
)
```

---

### Documentation

Documentation is available [here](https://python-amazon-sp-api.readthedocs.io/en/latest/)

[![Documentation Status](https://img.shields.io/readthedocs/python-amazon-sp-api?style=for-the-badge)](https://python-amazon-sp-api.readthedocs.io/en/latest/index.html)

### Consultation

Do you need help implementing? I offer consultation for everything SP-API related. 

[![Consultation](https://img.shields.io/badge/consultation-book-blue?style=for-the-badge)](https://calendly.com/michaelprimke/sp-api)


### Playground

[![playground](https://img.shields.io/badge/Playground-alpha-red?style=for-the-badge)](https://sp-api-playground.saleweaver.com/?utm_source=github&utm_medium=repo&utm_term=badge)

<sub>_The playground is a work in progress and currently in alpha. Please report bugs in this repository_</sub>


### New endpoints

You can create a new endpoint file by running `make_endpoint <model_json_url>`

```bash
make_endpoint https://raw.githubusercontent.com/amzn/selling-partner-api-models/main/models/listings-restrictions-api-model/listingsRestrictions_2021-08-01.json
```

This creates a ready to use client. Please consider creating a pull request with the new code.


### ADVERTISING API

You can use nearly the same client for the Amazon Advertising API. [@denisneuf](https://github.com/denisneuf) has built [Python-Amazon-Advertising-API](https://github.com/denisneuf/python-amazon-ad-api) on top of this client.
Check it out [here](https://github.com/denisneuf/python-amazon-ad-api)

### DISCLAIMER

We are not affiliated with Amazon


### LICENSE

![License](https://img.shields.io/github/license/saleweaver/python-amazon-sp-api?style=for-the-badge)

---

### Base Client

The client is pretty extensible and can be used for any other API. Check it out here:

[API Client](https://github.com/saleweaver/rapid_rest_client)

---
[![Quality gate](https://sonarcloud.io/api/project_badges/quality_gate?project=saleweaver_python-amazon-sp-api)](https://sonarcloud.io/summary/new_code?id=saleweaver_python-amazon-sp-api)

[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=saleweaver_python-amazon-sp-api&metric=sqale_rating)](https://sonarcloud.io/summary/new_code?id=saleweaver_python-amazon-sp-api)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=saleweaver_python-amazon-sp-api&metric=reliability_rating)](https://sonarcloud.io/summary/new_code?id=saleweaver_python-amazon-sp-api)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=saleweaver_python-amazon-sp-api&metric=coverage)](https://sonarcloud.io/summary/new_code?id=saleweaver_python-amazon-sp-api)


[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=saleweaver_python-amazon-sp-api&metric=bugs)](https://sonarcloud.io/summary/new_code?id=saleweaver_python-amazon-sp-api)
[![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=saleweaver_python-amazon-sp-api&metric=code_smells)](https://sonarcloud.io/summary/new_code?id=saleweaver_python-amazon-sp-api)
[![Technical Debt](https://sonarcloud.io/api/project_badges/measure?project=saleweaver_python-amazon-sp-api&metric=sqale_index)](https://sonarcloud.io/summary/new_code?id=saleweaver_python-amazon-sp-api)

[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=saleweaver_python-amazon-sp-api&metric=security_rating)](https://sonarcloud.io/summary/new_code?id=saleweaver_python-amazon-sp-api)
[![Lines of Code](https://sonarcloud.io/api/project_badges/measure?project=saleweaver_python-amazon-sp-api&metric=ncloc)](https://sonarcloud.io/summary/new_code?id=saleweaver_python-amazon-sp-api)
[![Duplicated Lines (%)](https://sonarcloud.io/api/project_badges/measure?project=saleweaver_python-amazon-sp-api&metric=duplicated_lines_density)](https://sonarcloud.io/summary/new_code?id=saleweaver_python-amazon-sp-api)

---
[![Downloads](https://static.pepy.tech/badge/python-amazon-sp-api)](https://pepy.tech/project/python-amazon-sp-api)
[![Downloads](https://static.pepy.tech/badge/python-amazon-sp-api/month)](https://pepy.tech/project/python-amazon-sp-api)
[![Downloads](https://static.pepy.tech/badge/python-amazon-sp-api/week)](https://pepy.tech/project/python-amazon-sp-api)
