# Credit Card Generator

Utility program to help you generate random *(dummy but technically valid)* credit cards for testing purposes.

[![Build Status](https://app.travis-ci.com/xcapdevila/creditcard-generator.svg?branch=main)](https://app.travis-ci.com/xcapdevila/creditcard-generator)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=xcapdevila_credit-card-generator&metric=alert_status)](https://sonarcloud.io/dashboard?id=xcapdevila_credit-card-generator)
[![Coverage Status](https://coveralls.io/repos/github/xcapdevila/credit-card-generator/badge.svg)](https://coveralls.io/github/xcapdevila/credit-card-generator)
[![Known Vulnerabilities](https://snyk.io/test/github/xcapdevila/credit-card-generator/badge.svg)](https://snyk.io/test/github/xcapdevila/credit-card-generator)

<br>

### Configuration details

Output file location. It may include **${now}** as placeholder and it will be replaced by the execution date time.
```
creditcard.generator.output-file=generated_credit_cards_${now}.csv
```

Output pattern. It may include the following placeholders:
- **${pan}** - it will be replaced by the generated pan
- **${cvv}** - it will be replaced by the generated cvv
- **${expDate}** - it will be replaced by the generated expiration date
- **${issuerName}** - it will be replaced by the issuer name
```
creditcard.generator.output-pattern=${pan},${cvv},${expDate},${issuerName}
```

Credit card issuers list to be generated including:
- **Name:** issuer name
- **Cards:** number of cards to be generated
- **PAN Regex:** regular expression to generate the PAN value
- **CVV Regex:** regular expression to generate the CVV value
- **Expiration Date Regex:** regular expression to generate the expiration date value
- **Luhn Compliant:** whether it must be luhn compliant or not
```
creditcard.generator.issuers[0].name=VISA
creditcard.generator.issuers[0].cards=100
creditcard.generator.issuers[0].pan-regex=^4[0-9]{15}$
creditcard.generator.issuers[0].cvv-regex=^[0-9]{3}$
creditcard.generator.issuers[0].exp-date-regex=^(0[1-9]|1[0-2])(2[2-7])$
creditcard.generator.issuers[0].luhn-compliant=true
```
<br>

### Usage
Compile the project using Maven
```
mvn clean package
```

Run it as a Java application either using its internal [application.properties](src/main/resources/application.properties) *(by default it's configured to generate 100 VISA cards)* 
```
java -jar target/generator-1.0.jar
```
or providing an external source with your custom configuration
```
java -jar target/generator-1.0.jar --spring.config.location=/Your/Path/custom_application.properties
```
<br>

### Reference docs
[Payment Card Number](https://en.wikipedia.org/wiki/Payment_card_number)

[Luhn Algorithm](https://en.wikipedia.org/wiki/Luhn_algorithm)

<br>

### Disclaimer

Use this piece of software under your own responsibility.
